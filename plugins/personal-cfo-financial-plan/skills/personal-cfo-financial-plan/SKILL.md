---
name: personal-cfo-financial-plan
description: Build or update a private, objective-led household financial plan from Personal CFO records, with optional budgeting and illustrative scenarios.
---

# Personal CFO Financial Plan

Use this skill after Personal CFO Setup and, ideally, an initial Lifestyle Review. It helps the household turn its verified financial record and stated objectives into a working plan. Conversation is the normal input: ask focused questions, use available evidence, and write only user-confirmed context and decisions under the hood. Do not ask the user to maintain a manual spreadsheet, ledger, or planning form.

This is planning support, not a professional advisory engagement. It does not execute transactions, recommend specific securities or insurance products, calculate a final tax liability, provide legal advice, or certify that an outcome is suitable or achievable.

## Start with the working session

Before examining account-level details, ask: “What financial objectives matter for this working session?” Ask whether this is a one-time decision, an annual plan, or an ongoing plan review. Work through each objective the user chooses and capture only what is useful: desired outcome, target timing, relative priority, constraints, and tradeoffs. Do not impose a generic goal list or assume a goal merely because data suggests one.

Reflect the objectives back in plain language and ask the user to confirm their priority order. State that current evidence and household context will inform the discussion but will not decide the objectives for them.

## Resolve the household record

Resolve the household's top-level folder from a Drive link or ID provided in this chat. Otherwise, find the exact native Google Doc `Personal CFO Home`, read its active-folder location, and verify that the locator belongs to that folder. Preserve `Personal CFO Home`; it is the durable locator, not a plan document. If the intended folder cannot be resolved unambiguously, ask the user for its link before reading household records.

Inside the resolved folder, read the exact native Google Doc `Personal CFO Household Context` when exactly one exists. Treat its rules, patterns, and user-added notes as labeled user-provided context. Apply a rule only within its stated scope; keep any mismatch as an ambiguity. Do not use Household Context to overwrite synced data or replace evidence for balances, benefits, insurance, tax, legal, or investment facts.

Use the exact `Transactional Data` subfolder for `Financial Data Warehouse` and sync exports. Before relying on the data, state the available transaction period, latest successful sync or export date, and material source or coverage gaps. Treat unavailable, stale, manual, and unsupported-provider values as gaps or explicitly dated evidence—not as zero, a closed account, or a complete picture. Ask the user to confirm the record's origin before using account-specific information in the plan.

Review supporting documents in the existing top-level folders only when they are relevant to the chosen objectives. For example, use benefits, insurance, debt, property, retirement, or legal records only when they materially affect the session. Ask the user to upload an existing document if a needed fact is absent and they want it considered; never ask for credentials or require manual data entry into a structured file.

## Establish the current position

Build a concise, evidence-labeled snapshot that is relevant to the selected objectives: observed cash flow and recurring commitments, assets and liabilities when supported, savings or debt patterns, and material gaps. Keep verified facts, user-confirmed planning assumptions, and unknowns visibly distinct. Household Context explains patterns; the warehouse and supporting documents remain the evidence for amounts and dates.

Ask the user to correct, defer, or leave unknown any material item before modeling it. Do not fill gaps with inferred balances, tax treatment, insurance coverage, estate intent, or investment assumptions.

## Offer a budget only when useful

After the current-position snapshot, explain whether a working budget would help the stated objectives. Ask: “Would you like to create a working budget as part of this plan?” The user may choose:

- **No budget for this plan** — continue with objectives, observed cash flow, and scenarios; record that a budget was not created.
- **Descriptive baseline** — summarize observed spending and known seasonal patterns without treating it as a target or limit.
- **Working budget** — develop an objective-linked target budget with the user.

For a descriptive baseline or working budget, derive the initial categories and amounts from the confirmed warehouse window and Household Context. Discuss seasonal or irregular costs and user-provided adjustments in conversation. A working budget must state its period, included categories, expected irregular or seasonal costs, and any intentionally unallocated amount. Present it for the user's confirmation before saving it. Never silently convert observed spending into a budget or ask the user to type amounts into a spreadsheet.

## Analyze options and scenarios

Use only scenarios that help the selected objectives. Compare the current path with one or more explicitly named alternatives, such as a changed savings amount, debt-paydown timing, a spending adjustment, or an objective timing change. State every material assumption, evidence date, uncertainty, and limitation. Show outcomes as illustrative ranges or conditional calculations when inputs are incomplete; do not present a projection as a guarantee.

Discuss tradeoffs and let the user select, defer, or reject each option. Frame possible next actions as a checklist for the user to consider, not as individualized financial, investment, tax, legal, or insurance instructions. When a decision needs specialist judgment, name the question and suggest consulting an appropriate qualified professional.

## Maintain the durable plan

`Personal CFO Financial Plan` is the household's third root-level durable document:

- `Personal CFO Home` is the machine-readable locator. Do not edit, rename, move, or delete it.
- `Personal CFO Household Context` is the reusable lifestyle and classification baseline.
- `Personal CFO Financial Plan` is the current objective-led plan baseline.

At the end of a planning session, summarize the session scope, prioritized objectives, evidence and data gaps, assumptions, budget choice, scenarios, tradeoffs, user decisions, and optional next steps. Ask for explicit confirmation before creating or updating the native Google Doc `Personal CFO Financial Plan` in the resolved top-level folder. If exactly one exists, update that document rather than creating another; if more than one exists, ask the user which is active. Verify the document's parent folder after writing.

Use these headings in this order:

1. **Plan metadata** — last plan date, session scope, data coverage, and material gaps.
2. **Current objectives and priorities** — user-confirmed objectives, timing, constraints, and priority order.
3. **Current position and evidence** — concise facts, evidence dates, and unresolved items.
4. **Budget status** — no budget, descriptive baseline, or confirmed working budget; include the period and any seasonal treatment when applicable.
5. **Planning assumptions and scenarios** — assumptions, alternatives considered, illustrative results, and limitations.
6. **Decisions and action checklist** — user-selected decisions and optional next actions.
7. **Open questions and next review** — deferred items, needed documents, specialist questions, and any review cadence the user explicitly chose.
8. **Plan history** — retain prior dated decisions and replaced assumptions as historical context; do not present them as current.

Use one concise bullet per item rather than dense paragraphs. Keep source facts, assumptions, and decisions labeled. Exclude credentials, account numbers, raw transaction identifiers, and unsupported sensitive inferences. Preserve prior plan history unless the user explicitly asks to remove it.

## Close and ongoing use

Summarize what the evidence supports, what the household chose, what remains unknown, and whether a budget was created. Remind the user that they can rerun Financial Plan to update the same durable document after a material change or a new planning session.

An existing recurring warehouse refresh keeps transaction evidence current; it does not update this plan. Once a plan exists, a future Financial Review workflow may compare refreshed evidence with objectives and an opted-in budget. Do not create a recurring plan review or automation unless the user explicitly requests it, and do not treat a data-refresh cadence as permission to interpret or change the plan.
