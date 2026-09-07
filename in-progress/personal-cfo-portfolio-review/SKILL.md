---
name: personal-cfo-portfolio-review
description: In-progress concept: review allocation, drift, concentration, and contribution-routing options without executing trades.
---
# Personal CFO Portfolio Review

Check investment freshness, account completeness, holdings completeness, and cost-basis availability. Group holdings by asset class, issuer, account type, and concentration. Compare with user-provided targets and drift bands; never invent targets. Consider cash needs, contributions, withdrawals, and upcoming liabilities. Prefer contribution-routing or observation-based alternatives. Return allocation, concentration, target-versus-current analysis, gaps, and non-executable options. Never produce an order ticket or claim a rebalance is required.

## Data-source bridge

Resolve the household's top-level budget-and-financial-information folder from an ID or Drive link the user gave in this chat. If none was provided, search connected Google Drive for the exact native Google Doc named `Personal CFO Home`, read its active folder ID, and verify the document belongs to that folder. Preserve this grounding document; do not delete, move, or overwrite it. Treat the resolved folder as the scope for uploaded files and supporting documents, and its exact `Transactional Data` subfolder as the scope for the warehouse and sync exports. If no valid locator or `Transactional Data` folder exists, or more than one valid locator exists, ask the user to identify the intended folder. Do not guess.

### Household context

Before interpreting transactions or related household records, look in the resolved top-level folder for the exact native Google Doc `Personal CFO Household Context`. If exactly one exists, read it as labeled user-provided context. Conversation with the relevant Personal CFO workflow is the standard way to update it; preserve any user-added household-contact notes. If it is missing, continue without one; if more than one exists, ask the user which is active. Apply a rule only when the record fits its stated scope, leave mismatches as ambiguous, and never use it to overwrite synced data or replace source evidence for balances, benefits, insurance, tax, legal, or investment facts.

Use the resolved `Transactional Data` folder as the financial-data handoff. Use the newest dated `Financial Warehouse Sync - YYYY-MM-DD` and the canonical `Financial Data Warehouse`; inspect `Sources`, `Accounts`, `Balance_Snapshots`, `Investment_Holdings`, `Investment_Transactions`, and `Sync_State`. Require current `snapshot_as_of` and source status before presenting allocation results. Preserve login-required or otherwise stale snapshots as incomplete coverage, not zero holdings.

Before presenting allocation or concentration results, summarize the export provenance and ask the user to confirm its origin. Existing confirmation in the current thread is sufficient for subsequent analysis.
