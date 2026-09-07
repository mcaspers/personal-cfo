---
name: personal-cfo-lifestyle-review
description: Lead a private, interactive household discussion of transaction patterns and durable, user-confirmed transaction-classification rules after Financial Warehouse Sync.
---

# Personal CFO Lifestyle Review

Use this skill after a successful Financial Warehouse Sync. It helps a household make sense of transaction patterns, resolve ambiguous expenses, and—only with the user's approval—maintain a durable lifestyle baseline for future Personal CFO work.

## Data-source bridge

Resolve the household's top-level budget-and-financial-information folder from a Drive link supplied in this chat. Otherwise, search connected Google Drive for the exact native Google Doc named `Personal CFO Home`, read its active folder location, and verify that the locator belongs to that folder. Treat the resolved folder as the only scope for the household's files, and its exact `Transactional Data` subfolder as the scope for its warehouse and sync exports.

Use the one active native Google Sheet named `Financial Data Warehouse` inside `Transactional Data`. If the locator, subfolder, or warehouse is missing, inaccessible, or ambiguous, ask the user for the intended link. Never create, move, replace, or infer a household record.

Before discussing account-specific details, look in the resolved top-level folder for the exact native Google Doc `Personal CFO Lifestyle Baseline`. If exactly one exists, read it before reviewing transactions and treat its confirmed rules as user-provided context. If it is missing, continue without one. If more than one exists, ask the user which baseline is active. Never use a baseline rule to overwrite synced data, infer a missing value, or replace source documents.

Treat the baseline as a living record. On a repeat Lifestyle Review, state that this review can refresh the existing baseline. Revisit relevant saved classification rules, category descriptions, cash treatment, and seasonal patterns; ask whether each is still current, should be changed, should be retired, or should be deferred. Do not remove a rule merely because it was not revisited, but retain its prior confirmation date so its age remains visible.

Before discussing account-specific details, inspect `Metadata`, `Sources`, `Sync_State`, recent `Sync_Runs`, and the `Transactions` headers. Summarize the available date range, most recent successful sync, and material coverage or source gaps. Ask the user to confirm the warehouse origin before substantive review unless it was already confirmed in this chat.

## Transaction and classification review

Read the complete available `Transactions` history in bounded date or row slices. When the user has not selected a period, focus the conversation on the most recent complete 90 days and compare the preceding equivalent period when coverage supports it.

Use the live headers instead of assuming a column order. Keep transaction IDs as text. Read amounts as numbers; when a numeric field is stored as text, call out the data-quality limitation and leave the sheet unchanged. Separate spending observations from transfers, card payments, refunds, reimbursements, and pending items whenever source fields support that distinction. If direction is ambiguous, discuss frequency and absolute amounts without calling the movement spending or income.

For every reviewed non-pending expense, decide whether its classification is clear for this review or needs confirmation. A classification is clear only when the provider category is specific and consistent with the transaction details, or a matching user-confirmed Lifestyle Baseline rule applies. Surface all other expenses as an ambiguity queue, including missing or generic categories, conflicting category and merchant details, unclear transfers, refunds or reimbursements, vague merchant descriptions, and transactions that could reasonably belong to more than one category.

Group equivalent ambiguous transactions by a stable merchant or description pattern. For each group, show the description, date range, count, total when reliable, current category, and the reason it is ambiguous. Do not guess a category or silently recategorize the warehouse. Work through no more than three groups in one turn, but continue until the user chooses to defer or resolve every surfaced group.

Treat cash separately as **Cash & Manual Spending**. Identify ATM withdrawals, cash withdrawals, and similar cash-funding transactions, but do not call a withdrawal an expense category unless the user has supplied supporting cash records. Ask whether the user wants to describe what cash normally funds, keep a simple cash log or receipts in the matching Drive folder, or leave the use of cash unclassified. Record only a user-confirmed reusable cash-treatment rule in the Lifestyle Baseline.

## Category-by-category lifestyle review

Create a review list from every spending category with activity in the period, plus Cash & Manual Spending when cash-funding transactions appear. Work through the categories one at a time; the user may defer any category. For each category, show its date range, transaction count, total when reliable, comparable-period change, ambiguous items, and any applicable confirmed baseline rules. Ask the user for a short description of what the category represents in their household and whether its normal level, frequency, or drivers need context. Keep that commentary distinct from transaction facts.

For categories with seasonal or recurring variation, ask whether the change is expected and what time period it applies to. Offer neutral examples only as prompts: spring or fall patterns, winter heating, holiday spending, summer travel or cooling costs, school or camp-related spending, and other household routines. Ask about children, camps, travel, household composition, home heating or cooling, and general climate or region only if the user wants to provide that context; never request an address, names, ages, diagnoses, or other private details. A seasonal pattern must name its affected category, period, expected direction or range when volunteered, and user-provided explanation before it is saved.

## Pattern scan

After the category review, identify at most three additional conversation candidates, selected from repeated merchants, cadence changes, unusual transactions relative to the household's own comparable history, or time/category clusters. For each candidate, state the category or grouping, date range, count, amount or change when reliable, comparison basis, and uncertainty. Label it as a data observation.

## Interactive conversation

Discuss one item at a time. For an ambiguous group, ask a neutral question such as: “How should future transactions matching this description be treated?” Clarify the category or transfer/refund treatment, the matching scope, and any important exception. The user may skip, correct, or defer. A reusable rule exists only after the user explicitly confirms how future matching transactions should be handled; a one-time explanation remains chat context unless the user asks to preserve it.

For pattern candidates, invite context with a short, neutral question such as: “I noticed [observation]. Does this reflect something in your life that would help interpret it?” Offer a skip, correction, or defer option.

Keep the household's explanation distinct from the data observation. Ask one focused follow-up only when the answer would materially change the interpretation. Retain corrections as chat context for this review. At the end, ask before saving user-confirmed reusable rules.

Do not infer health conditions, relationships, religion, politics, employment status, or other sensitive facts from merchant names or categories. Do not label spending as wasteful, necessary, healthy, or irresponsible. Do not ask for credentials, account numbers, documents, diagnoses, or other information the user has not volunteered.

## Save the Lifestyle Baseline

At the end, summarize the new, changed, retained, retired, and deferred classification rules; category descriptions; cash treatment; and seasonal context. Ask for explicit confirmation before creating or updating the native Google Doc `Personal CFO Lifestyle Baseline` in the resolved top-level folder. Do not create a second document with that name, and verify its parent folder after writing.

The baseline contains only user-confirmed, reusable household context and transaction rules. Record the baseline's last review date. For each rule, record the matching merchant or description pattern, the future classification or treatment, its scope and exceptions, and the confirmation date. For category context, record the category, the user's description, and any confirmed recurring or seasonal pattern. For cash, record whether withdrawals are intentionally left unclassified or the user-confirmed treatment and scope. Update confirmed changes in place, retire only rules the user explicitly retires, and preserve unreviewed rules with their existing confirmation date. Keep provider categories and synced facts unchanged. Exclude account numbers, balances, credentials, raw transaction identifiers, inferred sensitive information, and unconfirmed interpretations.

Future Personal CFO work uses this document as a labeled, user-provided baseline before interpreting transactions or related household records. It applies a rule only when the new record fits its stated scope, keeps any mismatch as an ambiguity, and never treats the baseline as an authoritative source for balances, benefits, insurance, tax, legal, or investment facts.

## Close the review

Summarize:

1. **Data observations** — what the transaction record supports.
2. **Confirmed household context and rules** — only information the user approved for future use.
3. **Open questions or data gaps** — including freshness, source status, and deferred classifications.

Offer user-selected next steps only when helpful, such as reviewing a category in a future period, checking whether a recurring charge is expected, or preparing a separate household report. Frame these as choices, not individualized financial, investment, tax, legal, or insurance instructions. Ask before creating a recurring review.

Tell the user: “To update this baseline later, rerun Personal CFO Lifestyle Review. The confirmed changes will update the same `Personal CFO Lifestyle Baseline` document for the other Personal CFO plugins to use.”
