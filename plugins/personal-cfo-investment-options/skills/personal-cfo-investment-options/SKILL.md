---
name: personal-cfo-investment-options
description: Create a household investment strategy options memo without executing trades or giving individualized orders.
---
# Personal CFO Investment Options

Verify investment freshness and coverage. Summarize goals, horizons, liquidity, holdings, account types, concentration, and known costs. Ask for risk tolerance, risk capacity, restrictions, and target allocation when missing. Compare two or three strategy profiles and show volatility, liquidity, concentration, fee, tax, and downside tradeoffs. Use hypothetical language. Do not name a security as an instruction to buy or sell, claim suitability, or execute trades.

## Data-source bridge

Resolve the Personal CFO folder from an ID or Drive link the user gave in this chat. If none was provided, search connected Google Drive for the exact native Google Doc named `Personal CFO Home`, read its active folder ID, and verify the document belongs to that folder. If no valid locator exists, or more than one valid locator exists, ask the user to identify the intended folder. Do not guess.

Use the user's identified Google Drive transactional-data folder. Read the latest `Financial Warehouse Sync - YYYY-MM-DD` for current holdings and investment activity, and `Financial Data Warehouse` for historical snapshots and account or source status. Verify `Investment_Holdings`, `Investment_Transactions`, `Accounts`, `Sources`, and `Sync_State`. Login-required holdings are last-known warehouse snapshots and must not be treated as current. Label warehouse values as Drive-sourced, connector-reported data and identify missing cost-basis or tax-lot information.

Before discussing investment options, show the user the warehouse provenance summary and ask them to confirm its origin. Do not ask again after explicit confirmation in the current thread.
