---
name: personal-cfo-client-review
description: Prepare a decision-oriented monthly or quarterly household financial review.
---
# Personal CFO Review

Compare the selected period with the prior period and prior year when possible. Identify material changes in balances, income, spending, debt, recurring costs, benefits, insurance, and investments. Separate spending from transfers, card payments, refunds, and reimbursements. Review documented plans and trigger dates in Drive. Produce what changed, what needs attention, decisions needed, questions for professionals, and dated next actions. Be direct without spinning outcomes. Recommendations are decision support only.

## Data-source bridge

Start with the user's identified Google Drive transactional-data folder. Use the newest dated `Financial Warehouse Sync - YYYY-MM-DD` for the current period and `Financial Data Warehouse` for prior-period comparisons. Validate `Sources`, `Sync_State`, transaction-date coverage, and account `connection_status` before calling a change material. Treat login-required or other stale snapshots as data limitations, not zero balances or missing accounts.

Before comparing household periods, summarize warehouse provenance and ask the user to confirm its origin. If already confirmed in the current thread, reuse that confirmation; otherwise do not present account-specific conclusions yet.
