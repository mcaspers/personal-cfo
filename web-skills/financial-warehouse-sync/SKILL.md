---
name: financial-warehouse-sync
description: Synchronize connected Finances data into the selected household Financial Data Warehouse in Google Drive. Use after Personal CFO Setup has created or identified the household folder.
---

# Financial Warehouse Sync — Hardened v2

## Web app scope

This is an upload-ready ChatGPT web skill for the first and later live imports of a household's connected Finances data. Use it only in ChatGPT on the web, where both Finances and Google Drive are connected and usable. Do not run it in the desktop app.

## Required readiness check and confirmation gate

At the beginning of every run, automatically perform a **read-only** Finances readiness check. Confirm that Finances has completed an account sync and can return at least a connection status, account count, or available-data period. Also verify that Google Drive can access the intended top-level folder and its selected spreadsheet.

Report the result in plain language without displaying account numbers, balances, or transactions. For example: "Finances is connected and data is available. I found your Financial Data Warehouse in your Personal CFO folder. Would you like me to sync it now?"

Do not create, initialize, modify, or populate the workbook until the user gives an explicit affirmative answer in this web chat. A confirmation given earlier to the desktop setup plugin does not satisfy this gate.

If Finances is not connected, has not finished syncing, or cannot return a read-only availability check, stop and tell the user to finish or wait for the Finances sync. Do not write an empty financial import and do not describe the record as ready. If Drive cannot resolve exactly one intended folder and workbook, stop and ask the user for its link.

## Resolve the setup-created location

Prefer a folder or spreadsheet link supplied in the current chat. Otherwise, look for the exact native Google Doc `Personal CFO Home` in the selected household folder and read its active-folder location. Treat that top-level folder as the only scope for the warehouse, uploaded files, and supporting documents. Do not search globally for similarly named folders.

## Canonical destination

Configured canonical Spreadsheet ID (when already provisioned): ``

Spreadsheet URL:
`https://docs.google.com/spreadsheets/d//edit`

Expected warehouse schema version: `v2`.
Current sync skill version: `v2.4-portable`.

Never create a replacement workbook during a normal sync.
Never accept a trashed warehouse as canonical.
Never bootstrap a replacement while a same-named warehouse in the target context is in Trash unless the user explicitly authorizes replacement. Once a canonical warehouse is resolved, update that warehouse in place.


## Portable configuration

This skill must not depend on any individual's spreadsheet IDs, folder IDs, institution names, account IDs, or manual-memory identifiers.

Runtime configuration:
- `warehouse_spreadsheet_id`: strongest identity when a canonical warehouse is already known;
- `target_folder_id` or `target_folder_url`: required top-level household budget-and-financial-information folder selected during Setup;
- `warehouse_name`: defaults to `Financial Data Warehouse`.

If no spreadsheet ID is configured, use bootstrap discovery.

Do not require the user to edit this skill merely to supply their own Drive IDs when the host environment supports runtime or persisted configuration.

Institution names may appear in source data, but no institution may be embedded here as a required verification sentinel.

## Bootstrap mode

The skill supports **bootstrap mode** for a fresh environment where the canonical warehouse does not yet exist.

### Discovery before creation

Before any sync, resolve the target folder **first**, then resolve the canonical warehouse **only within that folder**.

Target warehouse name:
`Financial Data Warehouse`

Discovery rules:

1. Resolve exactly one active target folder.
   - Use the `target_folder_id` or `target_folder_url` supplied by Setup.
   - Exclude trashed folders.
   - If it is absent, inaccessible, or ambiguous, **fail closed** and ask Setup to identify the household's top-level folder.
2. If Setup supplies `warehouse_spreadsheet_id` or a Google Sheet URL, fetch that exact Sheet and verify that it is native Google Sheets, not trashed, and inside the resolved target folder. If valid, use it as the canonical warehouse and skip name-based discovery. If it is a new, uninitialized sheet created by Personal CFO Setup, initialize that exact sheet in place using the bootstrap schema contract before importing facts. If it fails any check, stop and explain the mismatch; do not silently choose or create another workbook.
3. If Setup did not supply a Sheet, search only inside the resolved target folder for a native Google Sheet named exactly `Financial Data Warehouse`.
   - Restrict by parent folder ID.
   - Restrict to native Google Sheets.
   - Require `trashed = false`.
   - Do **not** accept a global Drive search result that merely has the right title.
4. If exactly one active matching warehouse exists inside the target folder, use it.
5. If multiple active matching warehouses exist inside the target folder, **fail closed** and report an ambiguity.
6. Separately check for same-named trashed warehouse candidates associated with the target folder.
   - If an otherwise matching warehouse exists in Trash, **fail closed**.
   - Report that the existing warehouse must be restored or explicitly replaced.
   - Do not treat a trashed file as canonical.
   - Do not silently create a replacement while a same-named trashed warehouse exists.
7. If warehouse lookup fails because of permissions, connector errors, unavailable Drive access, or an unresolved folder, **do not create a replacement**.
8. Create a new warehouse only when:
   - the target folder is positively accessible;
   - there are zero active matching warehouses inside it;
   - there are zero matching trashed candidates requiring recovery;
   - discovery completed without access or connector errors.

Never create a second warehouse merely because a lookup timed out, returned an access error, or found a matching file outside the resolved target folder.

### Folder handling

Use the target folder selected during Setup. Do not search for or create another folder by name. If that folder is inaccessible or ambiguous, stop before creating a workbook.

### Creating a new warehouse

When bootstrap is required, either use the valid empty Sheet supplied by Personal CFO Setup or create one native Google Sheet named `Financial Data Warehouse`.

For a supplied empty Sheet, preserve its identity and parent folder. For a newly created Sheet, immediately place it in the resolved target folder. In either case:

1. Re-read its Drive metadata and verify:
   - its parent folder is the resolved target folder;
   - it is not trashed;
   - its MIME type is native Google Sheets.
2. If placement verification fails, **stop bootstrap**. Do not initialize financial tables in a file whose destination is unresolved.
3. Record its spreadsheet ID and URL as the canonical warehouse for the run.
4. Create the complete v2 schema before writing financial facts.

Required tabs:

- `Transactions`
- `Metadata`
- `Sources`
- `Accounts`
- `Balance_Snapshots`
- `Asset_Snapshots`
- `Investment_Holdings`
- `Investment_Transactions`
- `Liabilities`
- `Recurring_Streams`
- `Data_Dictionary`
- `Sync_State`
- `Sync_Runs`

Do not create a simplified seven-tab demonstration workbook.

### Bootstrap schema contract

Create the physical stable-key columns required by the current skill contract.

At minimum:

#### Transactions
Must include `transaction_id`.

#### Sources
Must include:
- `source_key`
- `item_id`
- source/provider/status/provenance fields.

Stable key: `source_key`.

#### Accounts
Must include:
- `account_id`
- `item_id`
- account identity/status/provenance fields.

Stable key: `account_id`.

Manual accounts must still populate canonical `account_id` with their persistent manual identifier.

#### Recurring_Streams
Must include:
- `stream_id`
- `account_name`
- `item_id`
- `account_id`
- recurring fields
- `normalized_average_amount`
- `normalized_last_amount`
- `cash_flow_normalization_status`
- `source_as_of`
- `observed_at`
- `lifecycle_status`

Stable key: `stream_id`.

A freshly bootstrapped warehouse has no legacy recurring migration state.

#
#### Normalized recurring cash-flow semantics

Preserve provider-native recurring amounts exactly in raw fields.

Also expose:
- `normalized_average_amount`
- `normalized_last_amount`
- `cash_flow_normalization_status`

Canonical sign convention:
- positive = cash inflow to the user;
- negative = cash outflow from the user.

Determine normalization from `flow_type` / source direction semantics, not by blindly multiplying all provider amounts by `-1`.

If direction is ambiguous:
- leave normalized amount blank/null;
- set normalization status to `ambiguous`;
- do not infer direction from merchant name alone.

Suggested statuses:
- `normalized`
- `already_canonical`
- `ambiguous`
- `not_applicable`

Normalized fields are derived warehouse semantics and must never overwrite raw provider amounts.

### Balance_Snapshots
Must include:
- `account_id`
- `balance_as_of`
- `source_type`
- `source_as_of`
- `observed_at`

Stable snapshot key:
`account_id | balance_as_of | source_type`.

#### Investment_Holdings
Must include:
- `account_id`
- `security_id`
- `snapshot_as_of`
- `observed_at`

Stable snapshot key:
`account_id | security_id | snapshot_as_of`.

#### Investment_Transactions
Must include `investment_transaction_id`.

#
### Liability completeness reconciliation

Treat `Accounts` as the completeness control for debts and `Liabilities` as the detailed liability register.

For every active debt-bearing `Accounts.account_id` (mortgage, loan, line of credit, credit card, or other amount owed), require either:
1. a current `Liabilities` row with the same `account_id`; or
2. a current fallback `Liabilities` row with `liability_coverage_status=balance_only`.

Never reconcile by account name, institution, mask, or display label. Join by `account_id`.

If the source exposes a current authoritative account balance but no structured liability details:
- create or update a liability snapshot using that balance;
- set `liability_record_type=account_balance_fallback`;
- set `liability_coverage_status=balance_only`;
- preserve provenance;
- leave APR, due date, minimum payment, statement balance, and other unavailable terms blank/null;
- never estimate missing terms.

If structured liability details become available later, preserve prior balance-only evidence and add/update the structured snapshot under normal snapshot rules.

Compute `debt_accounts_without_liability_rows` every run.
Steady-state expectation is 0.

If nonzero:
- report each missing `account_id`;
- do not claim debt completeness;
- mark the liability dataset/run partial when safe fallback creation is impossible because required source balance data is unavailable.

### Liabilities
Must include:
- `account_id`
- `snapshot_as_of`
- `source_as_of`
- `observed_at`

Stable snapshot key:
`account_id | snapshot_as_of`.

#### Asset_Snapshots
Must include:
- `memory_id`
- `snapshot_as_of`
- `source_as_of`
- `observed_at`

Stable snapshot key:
`memory_id | snapshot_as_of`.

### Initialize Metadata

Set at minimum:

- `Dataset` = `Financial data warehouse`
- `Warehouse schema version` = `v2`
- `Bootstrap status` = `initialized`
- `Bootstrap created_at` = current ISO 8601 timestamp
- `Purpose` = portable structured financial warehouse for Google Drive / GPT workflows

### Initialize Sync_State

Create one row for each managed dataset with the current physical key and mode:

- `Transactions` — `upsert` — `transaction_id` — overlap 90
- `Investment_Transactions` — `upsert` — `investment_transaction_id` — overlap 90
- `Recurring_Streams` — `upsert_current_state` — `stream_id`
- `Balance_Snapshots` — `append_snapshot` — `account_id|balance_as_of|source_type`
- `Investment_Holdings` — `append_snapshot` — `account_id|security_id|snapshot_as_of`
- `Liabilities` — `append_snapshot` — `account_id|snapshot_as_of`
- `Accounts` — `upsert` — `account_id`
- `Sources` — `upsert` — `source_key`
- `Asset_Snapshots` — `append_snapshot` — `memory_id|snapshot_as_of`

For a new warehouse:
- `last_successful_sync` starts blank;
- `last_full_reconcile` starts blank;
- `schema_version` is `v2`;
- `skill_version` is `v2.4-portable`.

### Initialize Sync_Runs

Create the full v2 audit schema including:

- `run_id`
- `started_at`
- `completed_at`
- `mode`
- `status`
- `dataset`
- `rows_read`
- `rows_inserted`
- `rows_updated`
- `rows_unchanged`
- `error_summary`
- `checkpoint`
- `preflight_status`
- `source_key_duplicates`
- `destination_key_duplicates`
- `skill_version`
- `lock_expires_at`
- `diff_hash`
- `warehouse_schema_version`

### First-run behavior

A newly bootstrapped warehouse must perform a **full reconciliation**, never a delta reconciliation.

Reason:
- there is no trusted checkpoint;
- there is no existing event history;
- there is no prior snapshot state.

The first full reconciliation uses the normal safety contract:
- retrieve all currently available history in bounded slices;
- preserve manual memories as first-class inputs;
- preserve stale-but-known connector snapshots;
- compute a dry-run diff;
- write in canonical order;
- verify all stable keys;
- only then advance checkpoints.

### Bootstrap rollback behavior

If warehouse creation succeeds but schema initialization fails:

- do not treat the file as a valid canonical warehouse;
- mark `Metadata` bootstrap status as `failed` if possible;
- report the partially initialized spreadsheet;
- do not write financial facts into an incomplete schema.

If financial-data synchronization fails after schema initialization:
- keep the initialized warehouse;
- keep successful dataset writes/checkpoints according to normal partial-run semantics;
- record failures in `Sync_Runs`;
- do not create another warehouse on retry.

### Post-bootstrap idempotency

After the initial full reconciliation succeeds:

1. immediately run or recommend the normal delta acceptance test;
2. expect a near-no-op when the source has not materially changed;
3. future runs auto-detect and reuse the same warehouse rather than creating a new one.

### Destination verification

Every successful run must be able to report:
- canonical spreadsheet ID;
- canonical spreadsheet URL;
- resolved target folder ID or URL;
- confirmation that the warehouse is active (`trashed=false`);
- confirmation that the warehouse parent matches the resolved target folder.

If these conditions cannot be verified, the run must not report successful warehouse resolution.

### Canonical identity after bootstrap

Once a warehouse is created successfully, its spreadsheet ID is the strongest canonical identity.

Name-based discovery is only for initial resolution.

If the caller/runtime can persist configuration, store:
- spreadsheet ID;
- target folder ID;
- schema version.

On later runs, prefer the stored spreadsheet ID and verify it still resides in the intended folder.


## Safety model

The default operation is a **delta reconciliation**, not an append dump and not a destructive overwrite.

Every run has four phases:

1. **Preflight**
2. **Read + normalize**
3. **Dry-run diff**
4. **Write + verify + checkpoint**

A dataset MUST NOT be written if its preflight fails.

## Phase 1 — Preflight

Read these before fetching/writing facts:

- spreadsheet metadata and sheet names;
- `Metadata`;
- `Sync_State`;
- recent `Sync_Runs`;
- headers of every target dataset.

### Schema validation

For every dataset in `Sync_State`:

1. Read `stable_key`.
2. Split composite keys on `|`.
3. Verify every named key column physically exists in the target sheet.
4. Verify required provenance columns for snapshot datasets exist.
5. Verify the warehouse schema version is compatible.

If a declared key column is absent, **fail closed** for that dataset.

Never invent a composite identity when a provider/source identity is declared.

### Existing-key validation

For normal keyed rows:

- no blank stable key is allowed;
- no duplicate stable key is allowed.

Exception: the explicitly documented one-time `Recurring_Streams` legacy migration described below.

### Lightweight run lock

Before writing, inspect `Sync_Runs` for `status=started` with an unexpired `lock_expires_at`.

If an active lock exists, do not start a competing write.

If an old lock is clearly expired, mark that prior run failed/abandoned before proceeding.

Append a `started` record for each dataset before its first mutation.

## Phase 2 — Read and normalize source data

Use Finances to retrieve:

- linked accounts and connector health;
- financial memories/manual assets;
- transactions;
- recurring transactions;
- investment holdings;
- investment transactions;
- liabilities.

Preserve stale-but-known provider state.

A connector returning an error or no current detail does NOT mean:
- balance = 0;
- holding deleted;
- account deleted;
- old history should be removed.

### Normalization rules

Before comparing:

- preserve provider IDs exactly as strings;
- normalize blank/null consistently;
- use ISO 8601 timestamps;
- normalize dates to a canonical `YYYY-MM-DD` representation where only a date is known;
- keep timestamp precision when a real timestamp exists;
- compare money at source-currency precision;
- do not replace a higher-precision timestamp with a lower-precision date;
- serialize nested JSON deterministically before comparison;
- preserve raw/provider values separately when normalized equivalents also exist.

### Material-change comparison exclusions

For event and current-state tables, exclude sync-generated/warehouse metadata from equality checks.

At minimum exclude fields whose only purpose is ingestion/audit metadata, including:
- `observed_at`
- `snapshot_exported_at`
- `run_id`
- ingestion timestamps
- checkpoint fields
- diff hashes
- lock timestamps
- audit-only status timestamps generated by this sync

Do not count a row as updated merely because one of these fields changed.

When a row is classified as updated, record or report the names of the material fields that actually changed.
This is especially important for `Investment_Transactions` and `Transactions`.

## Phase 3 — Dry-run diff

No dataset is written until a diff is computed.

For every dataset compute:

- `rows_read`
- `rows_inserted`
- `rows_updated`
- `rows_unchanged`
- `rows_marked_stale_or_inactive`
- `source_key_duplicates`
- `destination_key_duplicates`

Also compute a deterministic `diff_hash` from the normalized planned mutations.

### Abort conditions

Abort that dataset before writing if:

- required key column is missing;
- unexpected blank keys exist;
- duplicate source keys exist;
- duplicate destination keys exist;
- a legacy-key migration is ambiguous;
- a current-state operation would unexpectedly remove a material percentage of rows without an explicit source/coverage explanation;
- source coverage indicates history is incomplete and the proposed plan would delete/retire history.

Record the failure in `Sync_Runs`.

## Dataset contracts

### Transactions

Stable key: `transaction_id`

Mode: `upsert`

Default query window:
`last_successful_sync - 90 days` through now.

Split into bounded date slices if connector row limits require it.

Include transfers.

Behavior:
- new key -> insert;
- existing key with normalized field changes -> update;
- unchanged -> no write;
- missing from current delta response -> no deletion.

A retry must be idempotent.

### Investment_Transactions

Stable key: `investment_transaction_id`

Mode: `upsert`

Use the same 90-day overlap concept.

Never remove previously captured investment activity solely because it is no longer returned.

### Recurring_Streams

Stable key: `stream_id`

Mode: `upsert_current_state`

**Never clear the tab before writing.**

Behavior:
- retrieve the complete current recurring stream set;
- upsert by `stream_id`;
- update mutable fields such as prediction, amounts, active state, account name, item ID, category, and description;
- if a previously known stream is absent, mark it `not_returned` or inactive only when the complete-source coverage is trustworthy;
- do not delete the historical row.

#### One-time legacy migration

The v1 warehouse contains legacy recurring rows created before `stream_id` was stored.

Those rows are marked `lifecycle_status=legacy_unkeyed`.

A sync may backfill them exactly once only when ALL of the following hold:

1. `stream_id` column exists.
2. Every legacy destination row maps to exactly one incoming source stream.
3. Every incoming candidate maps to at most one legacy destination row.
4. The deterministic migration tuple is unique on both sides.
5. No ambiguous pair exists.

Recommended migration tuple for the current warehouse:

`account_id | flow_type | description | merchant_name | frequency | normalized_last_amount`

This tuple is for migration only, never the long-term key.

If one-to-one uniqueness fails, abort `Recurring_Streams` without mutation.

After successful migration:
- populate `stream_id`;
- set `lifecycle_status=active` or the source-derived current lifecycle;
- fill missing `account_name` and `item_id`;
- record migration counts in `Sync_Runs`;
- thereafter require nonblank unique `stream_id` on every populated row.

Once no populated `Recurring_Streams` row has `lifecycle_status=legacy_unkeyed`, normal runs MUST NOT execute fuzzy/composite migration logic.

If `Sync_State.migration_policy = migration_complete`, legacy migration logic is disabled entirely for normal runs:
- require nonblank unique `stream_id`;
- do not evaluate migration tuples;
- do not attempt fuzzy/composite matching;
- fail closed if an unexpected unkeyed populated row appears.

Treat the legacy migration procedure as recovery-only documentation from that point forward.

### Sources

Stable key: `source_key`

Mode: `upsert`

`source_key` is the canonical physical identity for both connected and manual sources.
Do not substitute `item_id_or_source_name` or any other pseudo-key at runtime.

Update connector health in place.

Do not propagate connector failure into historical snapshot deletion.

### Accounts

Stable key: `account_id`

Mode: `upsert`

All warehouse account rows, including manual/unsupported-provider accounts, must expose a canonical physical `account_id`.
For manual rows, that field may contain the persistent manual identifier.
Do not use `account_id_or_persistent_account_id` as a declared key because it is a resolution rule, not a column.

Provider status/metadata are current-state fields.

Manual/unsupported provider accounts are first-class records.

### Balance_Snapshots

Stable snapshot key:
`account_id | balance_as_of | source_type`

Required provenance:
- `source_as_of`
- `observed_at`

Mode: `append_snapshot`

Definitions:
- `source_as_of`: timestamp/date supplied or implied by the source observation;
- `observed_at`: timestamp when the warehouse sync observed the record.

Append a new snapshot only if the snapshot identity is new or a new observation is materially meaningful under the source contract.

Never overwrite prior observations.

a disconnected/erroring source:
- preserve last-known balances;
- mark connector state separately;
- never replace stale known balances with zero/null because login is required.

### Investment_Holdings

Stable snapshot key:
`account_id | security_id | snapshot_as_of`

Required:
- `snapshot_as_of`
- `observed_at`

Mode: `append_snapshot`

Treat holdings as point-in-time facts.

Do not delete prior position snapshots when a position disappears from a later current snapshot.

If no source security ID exists, use a clearly documented deterministic fallback and mark it as fallback identity.

### Liabilities

Stable snapshot key:
`account_id | snapshot_as_of`

Required:
- `source_as_of`
- `observed_at`

Mode: `append_snapshot`

Append when material liability fields change, including APR, balance/statement, payment, due date, rate, escrow, or loan metadata.

Preserve old observations.

### Asset_Snapshots

Stable snapshot key:
`memory_id | snapshot_as_of`

Required:
- `memory_id`
- `source_as_of`
- `observed_at`

Mode: `append_snapshot`

Manual assets and debts are authoritative warehouse inputs and must not be erased by provider-only refreshes.

## Snapshot deduplication

Do not create meaningless repeated snapshots merely because a sync ran again.

Before appending, compare the latest row for the same logical entity/source.

Append when:
- source timestamp changed; or
- material value changed; or
- relevant status/freshness/provenance changed; or
- the source contract specifically requires recording a new observation.

Otherwise count it as unchanged.

## Timestamp precedence

When incoming and stored representations differ:

1. preserve the most precise valid timestamp;
2. normalize for equality comparison before diffing;
3. do not overwrite timestamp-with-time with date-only unless the source explicitly corrected it;
4. `observed_at` is never a substitute for `source_as_of`.


## Backward-compatible v2.4 column migration

This version keeps the warehouse schema family at `v2` and adds nullable columns non-destructively.

For existing warehouses, preflight may append these missing columns:

`Recurring_Streams`:
- `normalized_average_amount`
- `normalized_last_amount`
- `cash_flow_normalization_status`

`Liabilities`:
- `liability_record_type`
- `liability_coverage_status`
- `linked_asset_id`
- `linked_asset_memory_id`

Rules:
- append columns only;
- never clear or reorder existing data;
- preserve raw recurring amounts;
- backfill normalized recurring values only when direction is unambiguous;
- classify existing structured liability rows as `structured`;
- classify existing manual liability rows as `manual`;
- create balance-only fallback liability rows only through normal reconciliation using authoritative account balances.

Record this migration in the run audit/completion report.

## Write order

Use:

1. `Sources`
2. `Accounts`
3. `Transactions`
4. `Investment_Transactions`
5. `Recurring_Streams`
6. `Balance_Snapshots`
7. `Investment_Holdings`
8. `Liabilities`
9. `Asset_Snapshots`
10. verify all written datasets
11. advance `Sync_State`
12. finalize `Sync_Runs`

## Checkpoint semantics

`last_successful_sync` advances only after:

- write completed;
- destination reread succeeded;
- stable keys remain unique;
- inserted/updated counts match the plan;
- append-only sheet row count did not decrease;
- known historical sentinels still exist.

Do not advance a failed or partial dataset.

`last_full_reconcile` advances only after a successful full reconciliation.

## Full reconciliation

A full reconciliation is **non-destructive**.

Use it:
- weekly or monthly;
- after relink/repair;
- after schema migration;
- when source coverage/counts look suspicious.

For event history:
- retrieve the full currently available history in bounded slices;
- upsert all stable IDs;
- preserve previously captured rows that are no longer inside the provider's returned history.

For snapshot tables:
- append only genuinely new observations;
- never reconstruct fake historical snapshots from a current value.

For current-state tables:
- upsert current state;
- use status fields for missing/not-returned records where appropriate;
- do not clear-first.


### Versioning contract

Version the warehouse schema and the sync implementation independently.

- `warehouse_schema_version` / `Sync_State.schema_version` = `v2`
- current `skill_version` = `v2.4-portable`

A skill-version change does not imply a warehouse schema migration.
A warehouse schema version changes only when the physical/control-table contract changes incompatibly or requires a real schema migration.

Historical `Sync_Runs.skill_version` values must be preserved exactly as run-time facts.

## Sync_Runs requirements

Append one row per dataset per run with:

- `run_id`
- `started_at`
- `completed_at`
- `mode`
- `status`
- `dataset`
- `rows_read`
- `rows_inserted`
- `rows_updated`
- `rows_unchanged`
- `error_summary`
- `checkpoint`
- `preflight_status`
- `source_key_duplicates`
- `destination_key_duplicates`
- `skill_version`
- `lock_expires_at`
- `diff_hash`
- `warehouse_schema_version`

Version fields:
- `skill_version` records the exact sync-skill version that executed the run.
- `warehouse_schema_version` records the warehouse schema contract used by that run.

Statuses:
- `started`
- `success`
- `partial`
- `failed`

A retry should produce a new run record, not rewrite the prior audit record except to finalize its status.


### Portable preservation sentinels

Verification is data-driven, not institution-specific.

For every run:
- identify all pre-existing disconnected/erroring sources with last-known snapshots and verify those snapshots remain;
- identify all pre-existing manual or unsupported-provider accounts and verify they remain unless the user explicitly removed them;
- identify all pre-existing manual asset/debt snapshots and verify they remain unless superseded by a newer explicit manual snapshot;
- never require a particular bank, broker, insurer, mortgage company, employer, or account name to exist.

A newly bootstrapped warehouse may legitimately contain none of these categories.

## Verification

After every dataset write:

- reread affected stable-key columns;
- confirm no duplicates;
- confirm expected insert/update count;
- confirm known historical records remain;
- confirm snapshot table row count never decreased;
- confirm disconnected/erroring source last-known balances remain when connector is unhealthy;
- confirm all existing manual/unsupported-provider account and asset rows remain;
- verify no `legacy_unkeyed` recurring rows remain after a successful legacy migration.

## Hard prohibitions

Never:
- clear the workbook;
- clear `Recurring_Streams` before rewriting it;
- truncate historical snapshot sheets;
- silently invent a replacement identity for a missing provider key;
- interpret connector failure as zero;
- delete history because a current source response is shorter;
- overwrite manual data with provider absence;
- advance checkpoints before verification;
- continue writing after a schema/key preflight failure.

## Completion report

Report:
- run ID;
- mode;
- preflight result;
- per-dataset inserts/updates/unchanged;
- stale/inactive markings;
- connector warnings;
- migration counts if legacy migration occurred;
- whether disconnected/erroring source stale snapshots were preserved;
- whether full reconciliation is recommended.

## Idempotency acceptance test

After any successful full reconciliation, run an immediate delta reconciliation as an acceptance test.

Expected result when the source has not materially changed:
- 0 new event rows;
- 0 material updates on stable event/current-state rows;
- 0 new snapshots unless the source emitted a genuinely new as-of/value/status observation;
- overwhelmingly `unchanged` results.

If the immediate rerun produces material updates:
1. do not silently call the sync healthy;
2. identify the exact changed field names;
3. verify those fields are not sync-generated metadata;
4. verify timestamp/null/JSON normalization;
5. flag the dataset for investigation if the cause is not an actual source change.

A full reconcile followed by an immediate near-no-op delta is the production-readiness acceptance criterion.


## Share/install behavior

This portable skill is intended to work without source-code edits.

A new user should:
1. run Personal CFO Setup in the desktop app to create or identify the top-level household folder and spreadsheet;
2. open ChatGPT on the web, connect/authorize Finances and Google Drive, and wait for Finances to finish syncing;
3. upload and run this skill in the web app;
4. provide the Personal CFO folder or spreadsheet link when asked;
5. let the first run initialize the selected sheet and perform a full reconciliation;
6. use delta reconciliation for normal follow-up runs.

If the user already has a canonical warehouse, provide or persist its spreadsheet ID as runtime configuration when possible.


Completion reporting must include:
- `debt_accounts_total`
- `debt_accounts_with_structured_liabilities`
- `debt_accounts_with_balance_only_fallback`
- `debt_accounts_without_liability_rows`
- recurring streams normalized
- recurring streams with ambiguous cash-flow normalization
