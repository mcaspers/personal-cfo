# Research: Financial-advisor engagements and Personal CFO Financial Plan

**Date:** 2026-09-09  
**Scope:** Typical planning workflow and product boundaries, using CFP Board, SEC, and FINRA primary sources.

## Finding

The closest authoritative model is CFP Board's seven-step planning process:

1. Understand the client's personal and financial circumstances.
2. Identify and select goals.
3. Analyze the current course and alternatives.
4. Develop recommendations.
5. Present recommendations.
6. Implement them.
7. Monitor progress and update.

CFP Board's guidance treats the first five as the core planning work. Implementation and monitoring may be explicitly excluded from an engagement; otherwise their responsibility and cadence must be established. The guidance also illustrates using a balance sheet, cash flow, insurance and benefits, documented assumptions, and scenario/stress testing. [CFP Board: Guide to the Financial Planning Process](https://www.cfp.net/-/media/files/cfp-board/standards-and-ethics/compliance-resources/guide-to-financial-planning-process.pdf?hash=A8F02CC2451BE07E4FB05DE009A64F68&la=en)

## Fit with Personal CFO

| Advisor-process stage | Personal CFO Financial Plan role |
| --- | --- |
| Understand circumstances | Reuse the verified warehouse, supporting documents, and Household Context; show freshness, coverage, and gaps before relying on them. |
| Identify/select goals | Start every working session with: “What financial objectives matter for this session?” Capture horizon, priority, constraints, and tradeoffs. |
| Analyze alternatives | Compare the current path with explicitly named alternatives and stated assumptions; distinguish facts, user-confirmed assumptions, and unknowns. |
| Develop/present recommendations | Produce a durable, decision-oriented plan record: objectives, inputs, assumptions, scenarios, tradeoffs, risks, and an action checklist. |
| Implement | Provide an optional checklist only. Do not execute transfers, purchases, account changes, or policy actions. |
| Monitor/update | Offer an opt-in review cadence only after a plan record exists. A data-sync automation is separate from a financial-plan review. |

The existing warehouse and Household Context cover much of the information-gathering stage; they do **not** replace a goal-prioritization conversation. The Plan plugin should therefore begin with the user's working-session objectives rather than begin with a prefilled budget or a generic optimization.

## Product boundaries and implications

- Treat this as planning support, not a regulated advisory engagement. FINRA notes that “financial planner” has no standalone regulator and that service scope varies widely. State the plugin's scope and unresolved gaps rather than imply comprehensive professional advice. [FINRA: Financial Planners](https://www.finra.org/investors/investing/working-with-investment-professional/financial-planners)
- Keep the session scoped: ask whether this is a one-time decision, annual plan, or ongoing review. The SEC recognizes both one-time financial plans and ongoing portfolio-management relationships; monitoring must not be assumed. [SEC: Investment Adviser Fiduciary Duty Interpretation](https://www.sec.gov/rules-regulations/2019/06/ia-5248)
- Escalate rather than decide where a licensed or professional determination is needed—for example, individualized investment transactions, tax filing/position, legal/estate documents, or insurance suitability. FINRA describes the varied regulated roles that may be bundled under “financial planner.” [FINRA: Financial Planners](https://www.finra.org/investors/investing/working-with-investment-professional/financial-planners)
- Make traceability a first-class output: retain source dates, data gaps, assumptions, selected objectives, scenario results, recommendations and rationale, and user decisions/deviations. CFP Board's standards specifically call for documentation of these kinds of planning elements. [CFP Board: Financial Planning Practice Standards FAQ](https://www.cfp.net/ethics/compliance-resources/2020/01/financial-planning-and-application-of-the-practice-standards-for-the-financial-planning-process)

## Recommended first release shape

1. Confirm data foundation and plan-session scope.
2. Interview for prioritized objectives, time horizons, and constraints.
3. Build a current-state snapshot and clearly label evidence gaps.
4. Model a limited set of user-relevant, assumption-driven scenarios.
5. Save an agent-managed plan record and present a human-readable action checklist.
6. Offer—but never default to—recurring data refresh and later plan-review automation.

This keeps the public Financial Plan plugin focused on the advisor-process stages it can safely support: understanding, goal selection, analysis, and presentation. Implementation, monitoring, and specialist determinations remain explicit, user-controlled boundaries.
