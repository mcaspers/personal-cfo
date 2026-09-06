---
name: personal-cfo-client-report
description: Generate a source-labeled household financial report using connected financial data and verified Drive sources.
---
# Personal CFO Report

Create a monthly, quarterly, annual, or custom household report. Confirm the period, run data freshness and coverage checks, then summarize net worth, cash flow, debt, recurring commitments, protection, benefits, estate readiness, and investments. Compare periods only where supported. Include allocation or performance tables only when holdings and cash flows are complete enough. End with observations, uncertainties, professional-review questions, and dated actions. Never invent benchmarks or returns; do not make trades or tax or legal conclusions.

## Data-source bridge

Resolve the household's top-level budget-and-financial-information folder from an ID or Drive link the user gave in this chat. If none was provided, search connected Google Drive for the exact native Google Doc named `Personal CFO Home`, read its active folder ID, and verify the document belongs to that folder. Treat the resolved folder as the complete working scope for the warehouse, uploaded files, and supporting documents. If no valid locator exists, or more than one valid locator exists, ask the user to identify the intended folder. Do not guess.

Use the resolved top-level folder as the financial-data handoff. Prefer the latest dated `Financial Warehouse Sync - YYYY-MM-DD` export for the requested period and use `Financial Data Warehouse` for historical and normalized data. Check `Sync_State`, `Sources`, and source `observed_at` or `*_as_of` fields before reporting freshness. Label these values as Drive-sourced, connector-reported data. If a source is login-required or stale, show it as a limitation rather than filling the gap with an assumption.

Before using the warehouse in a report, show a brief provenance summary—export date, covered period, providers, and connector-status warnings—and ask the user to confirm its origin. Proceed without asking again only when that confirmation already exists in the current thread.
