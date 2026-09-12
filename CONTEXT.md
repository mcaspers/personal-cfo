# Personal CFO

This context defines the shared household-record concepts used by Personal CFO plugins.

## Language

**Personal CFO Household Context**:
The single native Google Doc in a household's top-level Personal CFO folder that records user-confirmed, reusable category, cash, seasonal, household-contact, and transaction-classification context. Conversation with a Personal CFO workflow is the standard way to add or update it; the agent writes confirmed details after approval. A household may also add or revise its own contact or context notes directly. Lifestyle Review refreshes the relevant context in place; it is interpretive context, not financial source evidence.
_Avoid_: lifestyle profile, transaction memory, manual ledger

**User-confirmed classification rule**:
A reusable instruction for future transactions matching a stated merchant or description pattern, including its treatment, scope, and exceptions. It does not alter the synced provider category.
_Avoid_: automatic recategorization, inferred rule

**Classification ambiguity**:
An expense whose current category or transaction details do not support one clear interpretation. It remains unresolved until the household confirms a rule or explicitly defers it.
_Avoid_: uncategorized expense, guessed category

**Cash & Manual Spending**:
The household category for cash-funding transactions and optional uploaded receipts or other supporting documents. A cash withdrawal funds spending and is not itself a classified expense without user-provided evidence. The household can explain cash use in conversation; it never needs to maintain a separate manual log.
_Avoid_: cash expense, ATM category

**Seasonal pattern**:
User-confirmed context describing a recurring time-bound change in a household spending category, its period, and its explanation. It is contextual interpretation, not a forecast or a source of financial facts.
_Avoid_: spending forecast, expected expense

## Planning orchestration

**Financial Plan**:
The household's objective-led planning record: its current priorities, relevant evidence, assumptions, scenarios, decisions, and open questions. It is the shared synthesis across planning domains, not a specialist opinion or a set of instructions to execute.
_Avoid_: master budget, financial advice

**Financial Plan Manager**:
The planning role that scopes a household decision, determines whether specialist planning work is relevant, and synthesizes the resulting briefs into the Financial Plan. It does not independently choose household priorities or make professional determinations.
_Avoid_: oversight agent, generalist adviser, router

**Specialist planning module**:
A bounded planning domain that examines a specific kind of household decision and returns a Specialist Brief for the Financial Plan Manager. It does not change the Financial Plan or execute a transaction on its own.
_Avoid_: sub-agent, expert agent, autonomous planner

**Specialist Brief**:
A decision-focused record from one specialist planning module that separates evidence, assumptions, unknowns, illustrative alternatives, tradeoffs, and professional-review questions. It informs the Financial Plan; it is not a final tax, legal, insurance, or investment determination.
_Avoid_: recommendation, specialist report, final answer

**Invocation trigger**:
A user question, material event, changed fact, or unresolved decision that makes a specialist planning module relevant to the current Financial Plan. A routine data refresh or the existence of a specialist is not, by itself, an invocation trigger.
_Avoid_: automatic run, default workflow

**Review state**:
The dated record of what a Specialist Brief considered, the evidence it relied on, and the conditions that would make it no longer current for a later decision. It prevents unnecessary repeat specialist work.
_Avoid_: agent memory, cached answer

**Cash Flow Strategy**:
The specialist planning domain for income and bill timing, recurring and irregular expenses, liquidity, and the household's capacity to fund its selected goals. It is broader than a budget, which is a user-confirmed spending target.
_Avoid_: cash flow strategist, budget agent, expense tracker

**Planning escalation**:
A clearly stated question that the household should take to an appropriate qualified professional because the available evidence cannot safely resolve it within planning support.
_Avoid_: referral, handoff failure
