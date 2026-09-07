---
name: personal-cfo-financial-plan
description: Build or update an assumption-driven household financial plan with cash-flow, debt, goal, and retirement scenarios.
---
# Personal CFO Financial Plan

Use connected data for current balances, transactions, recurring activity, debts, and investments. Identify missing assumptions such as ages, dependents, retirement timing, future income, taxes, inflation, savings, Social Security, pensions, insurance, housing, education, longevity, and external assets. Establish the balance sheet and cash flow, define goals and horizons, model base, downside, and upside cases, stress-test major risks, and rank actions by impact and urgency. Return assumptions, projections, scenarios, gaps, and an action checklist. Projections are illustrative; do not certify retirement readiness or make tax, legal, insurance, or investment determinations.

## Data-source bridge

Resolve the household's top-level budget-and-financial-information folder from an ID or Drive link the user gave in this chat. If none was provided, search connected Google Drive for the exact native Google Doc named `Personal CFO Home`, read its active folder ID, and verify the document belongs to that folder. Preserve this grounding document; do not delete, move, or overwrite it. Treat the resolved folder as the scope for uploaded files and supporting documents, and its exact `Transactional Data` subfolder as the scope for the warehouse and sync exports. If no valid locator or `Transactional Data` folder exists, or more than one valid locator exists, ask the user to identify the intended folder. Do not guess.

### Household context

Before interpreting transactions or related household records, look in the resolved top-level folder for the exact native Google Doc `Personal CFO Household Context`. If exactly one exists, read it as labeled user-provided context. Conversation with the relevant Personal CFO workflow is the standard way to update it; preserve any user-added household-contact notes. If it is missing, continue without one; if more than one exists, ask the user which is active. Apply a rule only when the record fits its stated scope, leave mismatches as ambiguous, and never use it to overwrite synced data or replace source evidence for balances, benefits, insurance, tax, legal, or investment facts.

Use the resolved `Transactional Data` folder as the financial-data fallback and handoff. Read the latest dated `Financial Warehouse Sync - YYYY-MM-DD` for current balances, transactions, recurring streams, liabilities, and holdings; use `Financial Data Warehouse` for normalized history and snapshots. Check `Sources`, `Sync_State`, and relevant `*_as_of` or `observed_at` fields. Separate warehouse facts from user-provided planning assumptions. Preserve stale, manual, or unsupported-provider values and model uncertainty explicitly.

Before building the balance sheet or scenarios, present the warehouse export date, covered period, provider list, and connector warnings and ask the user to confirm its origin. Do not treat the warehouse as the user's data source until confirmed in the current thread.
