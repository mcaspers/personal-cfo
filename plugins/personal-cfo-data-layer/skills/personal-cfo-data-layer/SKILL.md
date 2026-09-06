---
name: personal-cfo-data-layer
description: Build a source-aware household financial model from connected financial data and the user's Google Drive materials.
---
# Personal CFO Data Layer

Use connected financial sources for current accounts, balances, transactions, recurring activity, debts, and investments. Use the user's Drive folder for statements, policies, benefits, estate documents, manual assets, valuations, and authoritative registers.

## Financial-data warehouse bridge

Resolve the household's top-level budget-and-financial-information folder from an ID or Drive link the user gave in this chat. If none was provided, search connected Google Drive for the exact native Google Doc named `Personal CFO Home`, read its active folder ID, and verify the document belongs to that folder. Treat the resolved folder as the complete working scope for the warehouse, uploaded files, and supporting documents. If no valid locator exists, or more than one valid locator exists, ask the user to identify the intended folder. Do not guess.

The user's financial handoff must come from the resolved top-level folder. Before analysis, inspect that folder and use the newest active native Google Sheet named `Financial Data Warehouse` as the canonical warehouse. Also locate the newest dated `Financial Warehouse Sync - YYYY-MM-DD` sheet as the latest export snapshot. Do not rely on a global title search when a folder-scoped lookup is available.

### Provenance confirmation gate

After locating the transactional warehouse and before using account-specific facts, summarize the handoff: export date, covered period, source or provider names, connector statuses, and any stale or login-required sources. Ask the user to confirm its origin. Do not proceed with substantive household analysis until the user confirms, unless provenance was already explicitly confirmed in the current thread. If the warehouse is missing, empty, or its provenance is ambiguous, ask the user to identify or refresh the handoff rather than guessing.

Read the warehouse's `Metadata`, `Sources`, `Accounts`, `Balance_Snapshots`, `Asset_Snapshots`, `Investment_Holdings`, `Investment_Transactions`, `Liabilities`, `Recurring_Streams`, `Transactions`, and `Sync_State` tabs as relevant. Treat warehouse facts as Drive-sourced, connector-reported handoff and preserve `source_type`, `source_as_of`, `balance_as_of`, `snapshot_as_of`, `observed_at`, `connection_status`, and `quality_note`. Use the latest source observation—not the Drive file modified time alone—to determine freshness.

Source precedence: current direct financial-portal data when available and newer; otherwise the latest verified warehouse handoff; then statements; then illustrations or estimates; then assumptions. If direct access is unavailable in the current surface, continue from the warehouse and clearly report that limitation. Preserve stale-but-known or login-required account snapshots; never convert them to zero, delete their history, or treat missing current detail as account closure.

Before analysis: inventory sources; check freshness and reporting dates; build a register with entity, record type, value, as-of date, source, tier, confidence, and owner; reconcile conflicts explicitly. Keep historical values historical. Keep insurance cash value and policy loans separate. Label facts as connector-reported, Drive-sourced, calculated, user-provided, assumed, or unavailable. Do not expose unnecessary account numbers or make tax, legal, medical, insurance, or investment determinations.
