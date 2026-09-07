# Personal CFO

This context defines the shared household-record concepts used by Personal CFO plugins.

## Language

**Personal CFO Lifestyle Baseline**:
The single native Google Doc in a household's top-level Personal CFO folder that records user-confirmed, reusable category, cash, seasonal, and transaction-classification context. Lifestyle Review refreshes it in place; it is user-provided interpretive context, not financial source evidence.
_Avoid_: lifestyle profile, transaction memory

**User-confirmed classification rule**:
A reusable instruction for future transactions matching a stated merchant or description pattern, including its treatment, scope, and exceptions. It does not alter the synced provider category.
_Avoid_: automatic recategorization, inferred rule

**Classification ambiguity**:
An expense whose current category or transaction details do not support one clear interpretation. It remains unresolved until the household confirms a rule or explicitly defers it.
_Avoid_: uncategorized expense, guessed category

**Cash & Manual Spending**:
The household category for cash-funding transactions and the optional receipts or spending records that explain them. A cash withdrawal funds spending and is not itself a classified expense without user-provided evidence.
_Avoid_: cash expense, ATM category

**Seasonal pattern**:
User-confirmed context describing a recurring time-bound change in a household spending category, its period, and its explanation. It is contextual interpretation, not a forecast or a source of financial facts.
_Avoid_: spending forecast, expected expense
