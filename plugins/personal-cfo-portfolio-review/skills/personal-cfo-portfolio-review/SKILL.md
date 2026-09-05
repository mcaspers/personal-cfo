---
name: personal-cfo-portfolio-review
description: Review allocation, drift, concentration, and contribution-routing options without executing trades.
---
# Personal CFO Portfolio Review

Check investment freshness, account completeness, holdings completeness, and cost-basis availability. Group holdings by asset class, issuer, account type, and concentration. Compare with user-provided targets and drift bands; never invent targets. Consider cash needs, contributions, withdrawals, and upcoming liabilities. Prefer contribution-routing or observation-based alternatives. Return allocation, concentration, target-versus-current analysis, gaps, and non-executable options. Never produce an order ticket or claim a rebalance is required.

## Data-source bridge

Use the user's identified Google Drive transactional-data folder as the financial-data handoff. Use the newest dated `Financial Warehouse Sync - YYYY-MM-DD` and the canonical `Financial Data Warehouse`; inspect `Sources`, `Accounts`, `Balance_Snapshots`, `Investment_Holdings`, `Investment_Transactions`, and `Sync_State`. Require current `snapshot_as_of` and source status before presenting allocation results. Preserve login-required or otherwise stale snapshots as incomplete coverage, not zero holdings.

Before presenting allocation or concentration results, summarize the export provenance and ask the user to confirm its origin. Existing confirmation in the current thread is sufficient for subsequent analysis.
