---
name: personal-cfo-lifestyle-review
description: Lead a private, interactive household discussion of transaction patterns after Financial Warehouse Sync has populated the Personal CFO warehouse.
---

# Personal CFO Lifestyle Review

Use this skill after a successful Financial Warehouse Sync. It is a read-only conversation: it helps a household make sense of patterns in its transaction record and add the context that the data cannot supply. Do not write to Google Drive unless the user explicitly requests a separate saved artifact.

## Data-source bridge

Resolve the household's top-level budget-and-financial-information folder from a Drive link supplied in this chat. Otherwise, search connected Google Drive for the exact native Google Doc named `Personal CFO Home`, read its active folder location, and verify that the locator belongs to that folder. Treat the resolved folder as the only scope for the household's files, and its exact `Transactional Data` subfolder as the scope for its warehouse and sync exports.

Use the one active native Google Sheet named `Financial Data Warehouse` inside `Transactional Data`. If the locator, subfolder, or warehouse is missing, inaccessible, or ambiguous, ask the user for the intended link. Never create, move, replace, or infer a household record.

Before discussing account-specific details, inspect `Metadata`, `Sources`, `Sync_State`, recent `Sync_Runs`, and the `Transactions` headers. Summarize the available date range, most recent successful sync, and material coverage or source gaps. Ask the user to confirm the warehouse origin before substantive review unless it was already confirmed in this chat.

## Pattern scan

Read the complete available `Transactions` history in bounded date or row slices. When the user has not selected a period, focus the conversation on the most recent complete 90 days and compare the preceding equivalent period when coverage supports it.

Use the live headers instead of assuming a column order. Keep transaction IDs as text. Read amounts as numbers; when a numeric field is stored as text, call out the data-quality limitation and leave the sheet unchanged. Separate spending observations from transfers, card payments, refunds, reimbursements, and pending items whenever source fields support that distinction. If direction is ambiguous, discuss frequency and absolute amounts without calling the movement spending or income.

Identify at most three conversation candidates, selected from category changes, repeated merchants, cadence changes, unusual transactions relative to the household's own comparable history, time/category clusters, or records that need categorization or transfer clarification. For each candidate, state the category or grouping, date range, count, amount or change when reliable, comparison basis, and uncertainty. Label it as a data observation.

## Interactive conversation

Discuss one candidate at a time. Invite context with a short, neutral question such as: “I noticed [observation]. Does this reflect something in your life that would help interpret it?” Offer a skip, correction, or defer option.

Keep the household's explanation distinct from the data observation. Ask one focused follow-up only when the answer would materially change the interpretation. Retain corrections as chat context for this review, and ask before saving anything.

Do not infer health conditions, relationships, religion, politics, employment status, or other sensitive facts from merchant names or categories. Do not label spending as wasteful, necessary, healthy, or irresponsible. Do not ask for credentials, account numbers, documents, diagnoses, or other information the user has not volunteered.

## Close the review

Summarize:

1. **Data observations** — what the transaction record supports.
2. **Household context** — only explanations supplied by the user.
3. **Open questions or data gaps** — including freshness, source status, or categorization limits.

Offer user-selected next steps only when helpful, such as reviewing a category in a future period, checking whether a recurring charge is expected, or preparing a separate household report. Frame these as choices, not individualized financial, investment, tax, legal, or insurance instructions. Ask before creating a recurring review or saving notes.
