---
name: personal-cfo-lifestyle-review
description: Lead a private, interactive discussion of household transaction patterns after Financial Warehouse Sync has populated the Personal CFO warehouse.
---

# Personal CFO Lifestyle Review

Use this skill in ChatGPT on the web after a successful Financial Warehouse Sync. It is a read-only conversation: it helps a household make sense of transaction patterns and add the real-life context that data cannot supply. It does not make trades, move money, calculate tax liability, give legal advice, or write to Google Drive unless the user explicitly asks for a separate saved artifact.

## Locate the household record

Prefer a Personal CFO folder or `Financial Data Warehouse` link supplied in the current chat. Otherwise, resolve the exact `Personal CFO Home` locator, its active top-level folder, its `Transactional Data` subfolder, and the one active native Google Sheet named `Financial Data Warehouse` inside that subfolder. If the folder, subfolder, or warehouse is missing or ambiguous, stop and ask for the intended link. Never create, move, or replace anything.

Before discussing account-specific details, read `Metadata`, `Sources`, `Sync_State`, recent `Sync_Runs`, and the `Transactions` headers. State the available transaction-date range, whether the latest sync completed, and any material source or coverage gaps. Treat an unavailable or stale source as a data gap, not as zero spending or a closed account.

## Read and prepare the transaction record

Read the complete available `Transactions` history in bounded date or row slices before identifying patterns. Keep the review focused on the requested period when one is supplied; otherwise use the most recent complete 90 days and compare it with the preceding equivalent period when coverage permits.

Use the warehouse headers rather than assuming a fixed column order. Preserve provider IDs as identifiers. Read transaction amounts as numbers; if the warehouse exposes numeric-looking text, report the cell-type problem as a data-quality limitation and do not silently repair the workbook during this read-only review.

Separate spending observations from transfers, card payments, refunds, reimbursements, and pending items whenever the source fields support that distinction. Use provider sign semantics or a documented normalized amount only when available. If direction is ambiguous, discuss frequency and absolute amounts without calling a pattern spending or income.

## Pattern scan

Look for a small set of supported conversation candidates across the complete reviewed record:

- category changes, concentration, or unusual month-to-month variation;
- repeated merchants, newly recurring activity, or changes in purchase cadence;
- materially unusual transactions relative to the household's own comparable history;
- clusters in time, category, or merchant that may reflect an event, project, travel, seasonal activity, or a routine;
- incomplete categorization, duplicate-looking records, unclear transfers, or other limitations that could distort the picture.

Use the transaction evidence to make observations, not claims about the household. Do not infer health conditions, relationships, religion, politics, employment status, or other sensitive personal facts from merchant names or categories. Do not label a purchase as wasteful, necessary, healthy, or irresponsible.

Start with no more than three candidates. For each, give the category or merchant grouping, date range, count, amount/change when reliable, and the comparison basis. Mark the statement as an **observation** and state any relevant uncertainty.

## Interactive lifestyle conversation

Ask about one candidate at a time. Use a short, open invitation such as: “I noticed [observation]. Does this reflect something in your life that would help interpret it?” Offer a few neutral possibilities only as examples, and always include a way to skip, correct, or defer the question.

After each answer, separate the user-provided explanation from the transaction observation. Ask one focused follow-up only when it materially changes the interpretation. Do not interrogate the user, ask for credentials, or request documents, account numbers, diagnoses, or other information they do not volunteer.

When the user corrects a category, merchant identity, transfer classification, or interpretation, retain that correction as chat context for the current review. Ask before saving it anywhere. A user can choose to discuss one category, all candidates, or none.

## Close the review

Summarize in three clearly labeled parts:

1. **Data observations** — what the transaction record supports.
2. **Household context** — only the explanations the user supplied.
3. **Open questions or data gaps** — what remains uncertain, including source freshness or category quality.

Offer a short list of user-selected next steps only when useful, such as reviewing a category next month, checking whether a recurring charge is expected, or preparing a separate household report. Frame them as choices, not individualized financial instructions. Do not create a recurring review or save notes without explicit user approval.

