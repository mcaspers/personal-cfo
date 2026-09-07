---
name: personal-cfo-tax-review
description: Prepare a tax-professional review worksheet from financial and Drive data without making tax determinations.
---
# Personal CFO Tax Review

Inventory accounts, statements, tax forms, and relevant Drive documents. Identify potentially relevant interest, dividends, gains or losses, charitable activity, benefits, HSA activity, unusual transactions, and missing records. Separate observed transactions from tax classifications. Flag missing tax lots, carryforwards, spouse or retirement-account coverage, DRIPs, and external accounts. Produce questions, records to obtain, and deadlines to confirm. Do not calculate final liability or certify deductions, wash-sale status, capital-gain treatment, Roth eligibility, filing positions, or estate-tax exposure. Do not recommend a harvest or trade.

## Data-source bridge

Resolve the household's top-level budget-and-financial-information folder from an ID or Drive link the user gave in this chat. If none was provided, search connected Google Drive for the exact native Google Doc named `Personal CFO Home`, read its active folder ID, and verify the document belongs to that folder. Preserve this grounding document; do not delete, move, or overwrite it. Treat the resolved folder as the scope for uploaded files and supporting documents, and its exact `Transactional Data` subfolder as the scope for the warehouse and sync exports. If no valid locator or `Transactional Data` folder exists, or more than one valid locator exists, ask the user to identify the intended folder. Do not guess.

### Lifestyle baseline

Before interpreting transactions or related household records, look in the resolved top-level folder for the exact native Google Doc `Personal CFO Lifestyle Baseline`. If exactly one exists, read it as labeled user-provided context. If it is missing, continue without one; if more than one exists, ask the user which is active. Apply a rule only when the record fits its stated scope, leave mismatches as ambiguous, and never use it to overwrite synced data or replace source evidence for balances, benefits, insurance, tax, legal, or investment facts.

Begin with the resolved `Transactional Data` folder. Use the latest dated `Financial Warehouse Sync - YYYY-MM-DD` for current transactions, recurring streams, liabilities, accounts, holdings, and investment activity; use `Financial Data Warehouse` for normalized history and source status. Inspect `Sources`, `Accounts`, `Transactions`, `Investment_Transactions`, `Investment_Holdings`, `Liabilities`, and `Sync_State`. Treat warehouse rows as Drive-sourced, connector-reported observations, not tax classifications. Use `source_as_of`, `snapshot_as_of`, `balance_as_of`, and `observed_at` to establish evidence dates. Flag login-required sources, missing forms, missing tax lots, and unsupported external accounts without inferring tax results.

Before identifying tax-relevant activity, provide the user a provenance summary—export date, covered period, source or provider names, and connector warnings—and ask them to confirm its origin. Do not use it for account-specific tax-review observations until confirmed; reuse an explicit confirmation already given in the current thread.
