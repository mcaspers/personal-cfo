---
name: personal-cfo-lifestyle-review
description: Lead a private, interactive household review of transaction patterns and durable, user-confirmed transaction-classification rules after Financial Warehouse Sync.
---

# Personal CFO Lifestyle Review

Use this skill in ChatGPT on the web after a successful Financial Warehouse Sync. It helps a household make sense of transaction patterns, resolve ambiguous expenses, and—only with the user's approval—maintain durable household context for future Personal CFO work. Conversation is the primary input; the agent writes confirmed context rather than asking the household to maintain a manual ledger. It does not make trades, move money, calculate tax liability, or give legal advice.

## Locate the household record

Prefer a Personal CFO folder or `Financial Data Warehouse` link supplied in the current chat. Otherwise, resolve the exact `Personal CFO Home` locator, its active top-level folder, its `Transactional Data` subfolder, and the one active native Google Sheet named `Financial Data Warehouse` inside that subfolder. If the folder, subfolder, or warehouse is missing or ambiguous, stop and ask for the intended link. Never create, move, or replace anything.

## Choose the review window

At the beginning of the conversation, after resolving the warehouse and before reading transaction history or beginning a category discussion, ask: “How far back would you like to review for this household context—three months, six months, a year, all available history, or another period?” Do not assume a default period. Let the user choose a rolling lookback or a specific start and end date.

Read only the minimum metadata needed to state the available transaction-date range. If the chosen period is fully available, state the effective window and proceed. If it is partly unavailable, explain the coverage gap and ask whether to use the available portion, select another period, or stop. Keep the transaction, category, ambiguity, and pattern review within that window; do not expand it for an automatic comparison. If a comparison would be useful, offer one only when it can be made within the chosen window or the user explicitly expands the scope.

Look in the resolved top-level folder for the exact native Google Doc `Personal CFO Household Context`. If exactly one exists, read it before reviewing transactions and treat its confirmed rules and any user-added household-contact notes as user-provided context. If it is missing, continue without one. If more than one exists, ask the user which document is active. Never use a context rule to overwrite synced data, infer a missing value, or replace source documents.

Treat Household Context as a living record. On a repeat Lifestyle Review, state that this review can refresh the existing context. Present a compact list of saved rules, category descriptions, cash treatment, and seasonal patterns relevant to the selected window. Ask only about items contradicted by current evidence, implicated by an ambiguity, or selected by the user; retain other rules and their prior confirmation dates without re-confirming them individually. Preserve user-added household-contact notes unless the user asks to change or remove them.

Before discussing account-specific details, read `Metadata`, `Sources`, `Sync_State`, recent `Sync_Runs`, and the `Transactions` headers. State the available transaction-date range, whether the latest sync completed, and any material source or coverage gaps. Proceed from the resolved household record and invite a correction; ask the user for an action only when the record is ambiguous, unavailable, or materially incomplete. Treat an unavailable or stale source as a data gap, not as zero spending or a closed account.

## Transaction and classification review

Read the confirmed review window in bounded date or row slices before identifying patterns. Do not substitute a most-recent 90-day default or read transactions outside the effective window.

Use the warehouse headers rather than assuming a fixed column order. Preserve provider IDs as identifiers. Read transaction amounts as numbers; if the warehouse exposes numeric-looking text, report the cell-type problem as a data-quality limitation and do not silently repair the workbook during this read-only review.

Separate spending observations from transfers, card payments, refunds, reimbursements, and pending items whenever the source fields support that distinction. Use provider sign semantics or a documented normalized amount only when available. If direction is ambiguous, discuss frequency and absolute amounts without calling a pattern spending or income.

For every reviewed non-pending expense, decide whether its classification is clear for this review or needs confirmation. A classification is clear only when the provider category is specific and consistent with the transaction details, or a matching user-confirmed Household Context rule applies. Surface all other expenses as an ambiguity queue, including missing or generic categories, conflicting category and merchant details, unclear transfers, refunds or reimbursements, vague merchant descriptions, and transactions that could reasonably belong to more than one category.

Group equivalent ambiguous transactions by a stable merchant or description pattern. For each group, show the description, date range, count, total when reliable, current category, and the reason it is ambiguous. Do not guess a category or silently recategorize the warehouse. Work through no more than three groups in one turn, but continue until the user chooses to defer or resolve every surfaced group.

Treat cash separately as **Cash & Manual Spending**. Identify ATM withdrawals, cash withdrawals, and similar cash-funding transactions, but do not call a withdrawal an expense category unless the user has supplied supporting evidence. Ask the user in conversation whether to describe what cash normally funds or leave its use unclassified. They may upload existing receipts or other supporting documents in the matching Drive folder, but must not be asked to create a cash log, spreadsheet, or manual ledger. Record only a user-confirmed reusable cash-treatment rule in Personal CFO Household Context.

## Category-by-category lifestyle review

Create a review list from every spending category with activity in the confirmed window, plus Cash & Manual Spending when cash-funding transactions appear. First summarize routine categories whose data is clear and has no meaningful pattern or ambiguity, and let the user open any of them. Work through categories with an ambiguity, material change, seasonal pattern, or user-selected interest one at a time; the user may defer any category. For each focused category, show its date range, transaction count, total when reliable, changes supported within the selected window, ambiguous items, and any applicable confirmed baseline rules. Ask the user for a short description only when it would add reusable household context. Keep that commentary distinct from transaction facts.

For categories with seasonal or recurring variation, ask whether the change is expected and what time period it applies to. Offer neutral examples only as prompts: spring or fall patterns, winter heating, holiday spending, summer travel or cooling costs, school or camp-related spending, and other household routines. Ask about children, camps, travel, household composition, home heating or cooling, and general climate or region only if the user wants to provide that context; never request an address, names, ages, diagnoses, or other private details. A seasonal pattern must name its affected category, period, expected direction or range when volunteered, and user-provided explanation before it is saved.

## Pattern scan

Look for a small set of supported conversation candidates across the complete reviewed record:

- category changes, concentration, or unusual month-to-month variation;
- repeated merchants, newly recurring activity, or changes in purchase cadence;
- materially unusual transactions relative to the household's own comparable history;
- clusters in time, category, or merchant that may reflect an event, project, travel, seasonal activity, or a routine;
- incomplete categorization, duplicate-looking records, unclear transfers, or other limitations that could distort the picture.

Use the transaction evidence to make observations, not claims about the household. Do not infer health conditions, relationships, religion, politics, employment status, or other sensitive personal facts from merchant names or categories. Do not label a purchase as wasteful, necessary, healthy, or irresponsible.

After the category review, start with no more than three additional candidates. For each, give the category or merchant grouping, date range, count, amount/change when reliable, and the comparison basis. Mark the statement as an **observation** and state any relevant uncertainty.

## Interactive lifestyle conversation

Ask about one candidate at a time. Use a short, open invitation such as: “I noticed [observation]. Does this reflect something in your life that would help interpret it?” Offer a few neutral possibilities only as examples, and always include a way to skip, correct, or defer the question.

After each answer, separate the user-provided explanation from the transaction observation. Ask one focused follow-up only when it materially changes the interpretation. Do not interrogate the user, ask for credentials, or request documents, account numbers, diagnoses, or other information they do not volunteer.

For an ambiguous group, ask: “How should future transactions matching this description be treated?” Clarify the category or transfer/refund treatment, the matching scope, and any important exception. A reusable rule exists only after the user explicitly confirms how future matching transactions should be handled; a one-time explanation remains chat context unless the user asks to preserve it. A user can choose to discuss, defer, or skip any group.

## Save the Household Context

At the end, summarize the new, changed, retained, retired, and deferred classification rules; category descriptions; cash treatment; and seasonal context. Ask for explicit confirmation before creating or updating the native Google Doc `Personal CFO Household Context` in the resolved top-level folder. Do not create a second document with that name, and verify its parent folder after writing.

Household Context contains only user-confirmed, reusable household context and transaction rules, plus any household-contact notes the user has chosen to add. Use clear headings in this order: **Review metadata** (last review date, selected review window, and available data coverage); **Confirmed classification rules**; **Household patterns and seasonality**; **Needs confirmation**; and **Retired or historical context**. Keep any user-added household-contact notes in their own clearly labeled section. Within each section, use one bullet per rule, pattern, or open item—not dense compound paragraphs. A confirmed rule records its matching merchant or description pattern, treatment, scope and exceptions, and confirmation date when known. A household pattern records its category, user-provided explanation, and any recurring or seasonal period. A cash item records whether withdrawals are intentionally left unclassified or the user-confirmed treatment and scope. An item under **Needs confirmation** must state what is known and that it cannot be classified automatically. Retire only rules the user explicitly retires, preserve unreviewed rules with their existing confirmation date, and preserve user-added household-contact notes unless explicitly changed. Keep provider categories and synced facts unchanged. Exclude account numbers, balances, credentials, raw transaction identifiers, inferred sensitive information, and unconfirmed interpretations.

Future Personal CFO work uses this document as labeled, user-provided household context before interpreting transactions or related household records. It applies a rule only when the new record fits its stated scope, keeps any mismatch as an ambiguity, and never treats the context as an authoritative source for balances, benefits, insurance, tax, legal, or investment facts.

## Close the review

Summarize in three clearly labeled parts:

1. **Data observations** — what the transaction record supports.
2. **Confirmed household context and rules** — only information the user approved for future use.
3. **Open questions or data gaps** — what remains uncertain, including source freshness, category quality, and deferred classifications.

Offer a short list of user-selected next steps only when useful, such as reviewing a category next month, checking whether a recurring charge is expected, or preparing a separate household report. Frame them as choices, not individualized financial instructions.

After an initial Lifestyle Review, offer an **optional recurring data refresh**. Explain that it keeps the existing transaction warehouse current; it is separate from this review and will not change Household Context, classify transactions, gather documents, or make financial-plan decisions. Ask whether the user wants one. If yes, let them choose weekly, monthly, quarterly, yearly, or a custom cadence, then direct them to create a standalone task in [ChatGPT Scheduled](https://chatgpt.com/scheduled) on the web using Financial Warehouse Sync. The scheduled task must explicitly authorize only a non-destructive sync into the existing `Financial Data Warehouse` located through `Personal CFO Home`, and must report a connection or location problem without writing. Do not create a recurring review or scheduled write without explicit user approval.

Tell the user: “To update your household context later, rerun Personal CFO Lifestyle Review. The confirmed changes will update the same `Personal CFO Household Context` document for the other Personal CFO plugins to use.”
