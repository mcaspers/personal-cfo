---
name: personal-cfo-client-review
description: Prepare a decision-oriented monthly or quarterly household financial review.
---
# Personal CFO Review

Compare the selected period with the prior period and prior year when possible. Identify material changes in balances, income, spending, debt, recurring costs, benefits, insurance, and investments. Separate spending from transfers, card payments, refunds, and reimbursements. Review documented plans and trigger dates in Drive. Produce what changed, what needs attention, decisions needed, questions for professionals, and dated next actions. Be direct without spinning outcomes. Recommendations are decision support only.

## Data-source bridge

Resolve the household's top-level budget-and-financial-information folder from an ID or Drive link the user gave in this chat. If none was provided, search connected Google Drive for the exact native Google Doc named `Personal CFO Home`, read its active folder ID, and verify the document belongs to that folder. Preserve this grounding document; do not delete, move, or overwrite it. Treat the resolved folder as the scope for uploaded files and supporting documents, and its exact `Transactional Data` subfolder as the scope for the warehouse and sync exports. If no valid locator or `Transactional Data` folder exists, or more than one valid locator exists, ask the user to identify the intended folder. Do not guess.

### Household context

Before interpreting transactions or related household records, look in the resolved top-level folder for the exact native Google Doc `Personal CFO Household Context`. If exactly one exists, read it as labeled user-provided context. Conversation with the relevant Personal CFO workflow is the standard way to update it; preserve any user-added household-contact notes. If it is missing, continue without one; if more than one exists, ask the user which is active. Apply a rule only when the record fits its stated scope, leave mismatches as ambiguous, and never use it to overwrite synced data or replace source evidence for balances, benefits, insurance, tax, legal, or investment facts.

Start with the resolved `Transactional Data` folder. Use the newest dated `Financial Warehouse Sync - YYYY-MM-DD` for the current period and `Financial Data Warehouse` for prior-period comparisons. Validate `Sources`, `Sync_State`, transaction-date coverage, and account `connection_status` before calling a change material. Treat login-required or other stale snapshots as data limitations, not zero balances or missing accounts.

Before comparing household periods, summarize warehouse provenance and ask the user to confirm its origin. If already confirmed in the current thread, reuse that confirmation; otherwise do not present account-specific conclusions yet.
