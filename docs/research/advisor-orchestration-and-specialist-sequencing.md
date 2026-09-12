# Research: Advisor orchestration and specialist sequencing for the Financial Plan Manager

**Date:** 2026-09-12  
**Scope:** How a lead financial planner (and the software "orchestrator/worker" pattern) sequences, gates, coordinates, and synthesizes specialist work — product-design research for the Personal CFO Financial Plan Manager and its Specialist planning modules. This is not financial, tax, legal, or insurance advice.

## Finding

The Financial Plan Manager is best modeled on a lead financial planner running the CFP Board 7-step process, mapped onto the established software **orchestrator-workers** pattern: a coordinator owns objectives and synthesis, bounded workers own analysis and return structured briefs, and workers never act autonomously. This note extends the two existing research files — it does not restate them. It builds on the 7-step fit and boundaries in [financial-advisor-engagement-and-personal-cfo-plan.md](./financial-advisor-engagement-and-personal-cfo-plan.md) and the specialist taxonomy, shared brief contract, and release order in [specialist-domains-for-financial-planning.md](./specialist-domains-for-financial-planning.md). It fills six gaps those files left open: intake mechanics, relevance gating, cross-domain sequencing, synthesis and conflict resolution, review cadence and re-invocation, and the orchestration pattern with its tradeoffs.

The CFP Board's worked "Millers" example is the load-bearing evidence throughout: a real, illustrative sequence in which a planner elicits goals, reprioritizes them, identifies where specialists (CPA, attorney, insurance agent) are needed, models scenarios, stress-tests, and sets a monitoring cadence. [CFP Board: Guide to the 7-Step Financial Planning Process](https://www.cfp.net/-/media/files/cfp-board/standards-and-ethics/compliance-resources/guide-to-financial-planning-process.pdf)

---

## 1. Objective intake / discovery mechanics (7-step steps 1–2)

CFP Board splits the front of the process into **Step 1 — understanding the client's personal and financial circumstances** and **Step 2 — identifying and selecting goals**, where the professional must "Identify potential goals" and "Help the Clients select and prioritize goals." Intake gathers not just numbers but values: the Millers' worked example records "risk tolerance," "capacity for risk," "perceived risk," and separately their "time horizon, available assets, and need for income," plus "Values, Attitudes, Expectations." [CFP Board Guide, Steps 1–2](https://www.cfp.net/-/media/files/cfp-board/standards-and-ethics/compliance-resources/guide-to-financial-planning-process.pdf)

What makes a goal **well-formed**, from the example, is that each goal carries four attributes that intake must elicit explicitly:

| Attribute | Evidence from the worked example |
| --- | --- |
| **Horizon** | Goals bucketed as "Near Term / Mid Term / Long Term"; the cabin goal is renegotiated from "within the next decade" to a specific "six years." |
| **Amount / target** | "$150,000 lake cabin, with no mortgage"; college "current estimated annual cost of $71,000." |
| **Priority** | Clients "work with Joe to develop the following prioritization" — an ordered 1–5 list. |
| **Constraints & tradeoffs** | Planner flags that acquiring the cabin in six years "may be unrealistic" and that a pricier college "will have a negative effect on their other goals." |

Two intake mechanics matter for product design. First, the planner **surfaces goals the client did not raise**: analysis shows the Millers "do not have adequate insurance coverage and do not have an estate plan," so the planner adds those as goals. Intake is generative, not just a transcription of the client's stated wish list. Second, the planner **addresses incomplete information** as a first-class step — the Millers are "not sure who they listed as beneficiaries," and the planner asks them to retrieve it and to estimate cabin carrying costs "they had not considered." [CFP Board Guide, Step 1](https://www.cfp.net/-/media/files/cfp-board/standards-and-ethics/compliance-resources/guide-to-financial-planning-process.pdf)

Prioritizing **conflicting** goals is done collaboratively, and the final ranking can diverge sharply from the order the client first volunteered: the Millers raised cabin, college, and retirement, but the agreed priority put "adequate insurance coverage" at #1 and "estate plan" at #2 — foundational protection ahead of the aspirational goals — while retirement, a 35-year horizon, ranked #5. The planner also honors an informed client override: the Millers remain "adamant" about the elite university despite its drag on other goals. [CFP Board Guide, Step 2](https://www.cfp.net/-/media/files/cfp-board/standards-and-ethics/compliance-resources/guide-to-financial-planning-process.pdf)

**Product implication.** The Financial Plan Manager's intake should treat a goal as a structured object — {horizon, target amount, priority rank, constraints, explicit tradeoffs} — not a free-text wish, and should refuse to route analysis until those fields exist. It should do two things a naive router would skip: (a) propose gap-goals the household did not state (protection, continuity) and (b) log an "incomplete information" list that becomes retrieval tasks. The prioritization ranking, not the raw request order, is what routes which Specialist planning module runs first, and an informed household override must be recorded, not silently corrected. This deepens the "start with the session's objectives" guidance already in the engagement file rather than repeating it.

---

## 2. Invocation / relevance gating

A lead planner brings in a specialist domain only when **facts or events trigger it**, and declines work outside the agreed scope. Two authorities anchor this.

The SEC's fiduciary-duty interpretation makes scope contractual and duty-of-care scope-dependent: "the adviser and its client may shape that relationship by agreement," and "the specific obligations that flow from the adviser's fiduciary duty depend upon what functions the adviser … has agreed to assume." [SEC Commission Interpretation (IA-5248), Federal Register text](https://www.govinfo.gov/content/pkg/FR-2019-07-12/html/2019-12208.htm) A planner is not obligated — and under a bounded engagement is not authorized — to analyze domains the engagement did not scope in.

FINRA reinforces that no single credential or regulator defines a "financial planner": "The financial planning profession doesn't have its own regulator," planners "might have no financial credentials at all," and they may separately be "Brokers or investment advisers" or "Insurance agents or practicing accountants." The domains that need a licensed role (securities advice, insurance suitability, accounting/tax practice, legal drafting) are exactly the ones a generalist must recognize and route out, not perform. [FINRA: Financial Planners](https://www.finra.org/investors/investing/working-with-investment-professional/financial-planners)

The Millers example shows real-world **Invocation triggers** in action — a specialist is engaged because a fact or gap appears, not by default:

| Observed fact / event (trigger) | Domain it invokes | What the planner does NOT do |
| --- | --- | --- |
| No adequate insurance; home and cars present low-frequency/high-cost risk | Risk & insurance | Names coverage need; offers to "help … shop"; declines an umbrella policy "at this time" given net worth — a scoped-out decision, not a product sale |
| No estate plan; unknown 401(k)/insurance beneficiaries | Estate & continuity | Flags document and beneficiary gaps; leaves drafting/validity to a licensed attorney |
| Investments, taxable/tax-deferred accounts, asset-location questions | Tax / benefits & retirement | Applies "reasonable assumptions for … tax rates"; does not certify a position or file |
| Client asks about bitcoin / meme stocks | (No trigger) | Provides information but "does not change his recommendation" — a fact request is not an Invocation trigger |

The last row matters: the CONTEXT.md definition already says "A routine data refresh or the existence of a specialist is not, by itself, an invocation trigger," and the worked example demonstrates the same discipline — a passing question about an asset class did not spin up individualized security-selection work.

For the tax module specifically, the gate is legal, not merely stylistic: the IRS defines "practice before the IRS" to include preparing/filing documents and rendering written tax advice, so the Tax Strategy module must organize facts and questions and escalate, never represent the household. [IRS: practice before the IRS FAQ](https://www.irs.gov/tax-professionals/frequently-asked-questions)

**Product implication.** Relevance gating is a decision the Financial Plan Manager makes from evidence, expressed as a checklist of Invocation triggers per Specialist planning module (e.g., "self-employment income present → Tax Strategy relevant"; "minor dependent or no will on file → Estate & Continuity relevant"). Absent a trigger, the module does not run — this is both a token-cost control (§6) and a fiduciary-scope discipline. Each module's charter should carry an explicit "out of scope / escalate" boundary mirroring the FINRA/SEC/IRS lines, feeding the Planning escalation concept.

---

## 3. Sequencing & dependencies between domains

The worked example shows a natural ordering in which understanding the household's **cash position comes first** and feeds everything downstream. The planner's Step-3 analysis leads with cash-flow facts — the Millers "Have a cash reserve," "Do not have significant liabilities and have no credit card debt" — before evaluating any goal-funding or protection move. Recommendations are then repeatedly justified by their **cash-flow effect**: "A lower interest rate will decrease costs and increase cash flow," "Increases discretionary cash flow," and, conversely, "a disadvantage is the reduced cash flow resulting from the cost of ongoing" coverage. [CFP Board Guide, Steps 3–4](https://www.cfp.net/-/media/files/cfp-board/standards-and-ethics/compliance-resources/guide-to-financial-planning-process.pdf)

The example also demonstrates that goal funding is scheduled against liquidity and horizon: additional savings needed for the cabin is timed to "the six-year desired time frame," and college and retirement each get horizon-appropriate treatment ("17-year time horizon until college," "35 years" to retirement). Tax, insurance premiums, and debt service all show up as **cash-flow line items** that either free up or consume the household's capacity to fund goals — i.e., they interact through the cash-flow constraint rather than independently.

This confirms and extends the release order already argued in the specialist-domains file (Cash Flow Strategy first, then Tax, then Debt & Credit). The dependency logic, stated as a sequence:

1. **Cash Flow Strategy** establishes liquidity, timing, and unallocated cash — the substrate. (Consistent with CFPB treating cash-flow tracking of income, resources, and expenses as the starting point. [CFPB: Cash Flow Budget Tool](https://files.consumerfinance.gov/f/documents/cfpb_your-money-your-goals_cash_flow_budget_tool_2018-11_ADA.pdf))
2. **Tax events and Debt** are evaluated as claims on that cash flow (estimated payments, payoff/refinance change monthly cash flow and reserve needs).
3. **Goal funding** (cabin, college, retirement) is then sequenced by priority rank and horizon against remaining capacity.
4. **Protection** (insurance, estate/continuity) is sized against the plan's cash flow and the downside it must survive.

**Product implication.** The Financial Plan Manager should run **Cash Flow Strategy before** any goal-funding, tax, or debt module and pass its dated baseline forward as a shared input every later module consumes. Later-module briefs should express their effect in a common currency — change to monthly/annual cash flow and to reserve adequacy — so the Manager can net them. A module invoked out of order without the cash-flow baseline should be blocked, because its scenarios would lack the constraint that makes them comparable.

---

## 4. Cross-domain synthesis & conflict resolution

Specialist inputs routinely pull in different directions — pay down debt vs. fund a near-term goal vs. hold a tax reserve vs. buy protection. The worked example resolves this the way the Financial Plan Manager should: the **lead** (not any specialist) reconciles them against the agreed goal priority, states each recommendation's advantages and disadvantages in the same cash-flow terms, and tests whether they must be implemented together. Step 4 requires the planner to consider, for each recommendation, the "Assumptions and estimates," the "Basis," the "Timing and priority," and "Whether the recommendation is independent or must be implemented with another." In the example the planner concludes the recommendations "are independent and do not need to be implemented with other recommendations" — an explicit dependency check, not an assumption. [CFP Board Guide, Step 4](https://www.cfp.net/-/media/files/cfp-board/standards-and-ethics/compliance-resources/guide-to-financial-planning-process.pdf)

Conflicts are surfaced, not hidden: the planner tells the Millers the cabin-in-six-years goal pressures retirement and college saving, and that a pricier college hurts other goals — then lets the informed client decide. Synthesis therefore preserves the tradeoff and the client's choice rather than optimizing it away.

**Traceability** is a first-class expectation. The planner "documents the recommendations and basis … in his firm's Client record-keeping system" and, in doing so, "captures the assumptions and estimates that he used." Presentation reviews "the assumptions and calculations" with the client and confirms the goal list is "complete and accurate." CFP Board's Practice Standards make documentation of these planning elements — data, assumptions, recommendations and rationale, and client decisions — an ongoing requirement. [CFP Board Guide, Steps 4–5](https://www.cfp.net/-/media/files/cfp-board/standards-and-ethics/compliance-resources/guide-to-financial-planning-process.pdf) [CFP Board: Practice Standards / documentation FAQ](https://www.cfp.net/ethics/compliance-resources/2020/01/financial-planning-and-application-of-the-practice-standards-for-the-financial-planning-process)

**Product implication.** The Financial Plan is the single synthesis point; a Specialist Brief never edits it. The Manager reconciles conflicting briefs by (a) ranking against the household's agreed goal priority, (b) expressing each brief's effect in the shared cash-flow/reserve currency so they can be netted, (c) running an explicit dependency check ("independent" vs. "must-pair") before presenting, and (d) preserving — never auto-resolving — a live tradeoff, recording the household's decision. Every incorporated element must carry its evidence date, assumption, rationale, and the decision or override, so the plan is auditable. This operationalizes the Specialist Brief contract (evidence / facts-assumptions-unknowns / alternatives / escalation questions / user decision) already defined in the specialist-domains file.

---

## 5. Monitoring / review cadence & re-invocation

Monitoring is **Step 7**, and it is conditional, not automatic. The engagement file already establishes that implementation and monitoring can be excluded; this note adds the trigger mechanics. The SEC interpretation ties the duty to monitor to scope and duration: "the scope of the duty to monitor will be indicated by the duration and nature of the agreed advisory arrangement," and for "a one-time financial plan for a one-time fee, the adviser is unlikely to have a duty to monitor," whereas an ongoing, asset-based relationship carries relatively extensive monitoring. [SEC IA-5248, Federal Register text](https://www.govinfo.gov/content/pkg/FR-2019-07-12/html/2019-12208.htm)

Re-invocation is driven by a **changed fact or material event**, not a calendar refresh. The worked example ties re-work to life change: the planner notes life and disability insurance "needs may change as circumstances in their lives change; therefore, Joe should monitor … so that the recommendations may be updated when appropriate." The Review state concept in CONTEXT.md captures exactly this — a dated record of "the conditions that would make it no longer current." [CFP Board Guide, Step 5 (insurance monitoring note)](https://www.cfp.net/-/media/files/cfp-board/standards-and-ethics/compliance-resources/guide-to-financial-planning-process.pdf)

**Product implication.** The Financial Plan Manager should offer a review cadence only after a plan exists and only as opt-in, distinct from any data-sync automation. Each Specialist Brief should close by writing its Review state: the evidence dates it relied on and the specific changed facts (new income source, marriage/birth, home purchase, liquidity event, law change) that would make it stale. A routine transaction sync updates the warehouse but does **not** by itself re-invoke a module; only a material event matching a recorded staleness condition does. This prevents unnecessary repeat specialist work while still catching the events that genuinely warrant it.

---

## 6. Software orchestration pattern (and its tradeoffs)

The design maps cleanly onto Anthropic's **orchestrator-workers** workflow: "a central LLM dynamically breaks down tasks, delegates them to worker LLMs, and synthesizes their results," suited to "complex tasks where you can't predict the subtasks needed" because "subtasks aren't pre-defined, but determined by the orchestrator based on the specific input." [Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) That is precisely the Financial Plan Manager's job: which Specialist planning modules are relevant is decided per household from the intake, not fixed in advance.

The multi-agent research write-up describes the coordination contract the Manager should copy: the lead "analyzes it, develops a strategy, and spawns subagents," each worker receives "an objective, an output format, guidance on the tools and sources to use, and clear task boundaries," and afterward the lead "synthesizes these results and decides whether more research is needed." [Anthropic: How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system) The Claude Agent SDK gives the mechanics: workers are defined by a `description` (when to use it), a bounded `prompt`, and a restricted `tools` set; they run in **context isolation** where "only its final message returns to the parent," and independent workers run in **parallel**. Tool restriction is the technical enforcement of "workers don't act autonomously" — a read/analyze-only module simply "gets `["Read", "Grep", "Glob"]`" and no write/execute tools. [Claude Agent SDK: Subagents](https://code.claude.com/docs/en/agent-sdk/subagents)

Mapping to the plugin vocabulary (note: "Specialist planning module," not "sub-agent," in user-facing framing):

| Orchestrator-worker element | Personal CFO element |
| --- | --- |
| Coordinator owns objectives, decomposition, synthesis | **Financial Plan Manager** owns intake, relevance gating, sequencing, and the **Financial Plan** |
| Worker gets objective + output format + boundaries | **Specialist planning module** gets a scoped decision question and the shared brief contract |
| Worker returns structured result; lead synthesizes | Module returns a **Specialist Brief**; only the Manager incorporates it |
| Tool restriction / read-only workers | Module analyzes and questions; it never executes a transaction or edits the plan |
| Context isolation; only final message returns | Module's working detail stays in the module; the Brief is the interface |

**Tradeoffs the design must respect.** Multi-agent orchestration is expensive: multi-agent systems "use about 15× more tokens than chats," so they are worth it only for high-value, breadth-heavy work; the same team warns that under-specified agents "duplicate work, leave gaps," and that early systems would "spawn 50 subagents for simple queries." [Anthropic: Multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system) The effective-agents guidance is to find "the simplest solution possible, and only increasing complexity when needed," noting that "optimizing single LLM calls" is often enough and that agentic systems "trade latency and cost for better task performance." [Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) The SDK exposes real spawn-depth, concurrency, and spend caps for the same reason. [Claude Agent SDK: Subagents](https://code.claude.com/docs/en/agent-sdk/subagents)

**Product implication.** Relevance gating (§2) is not only a fiduciary discipline — it is the primary cost control: a Specialist planning module runs only on an Invocation trigger, which is the domain analog of "don't spawn 50 subagents for a simple query." For a single, well-scoped household question (e.g., "can we afford this month's bills?"), the Manager should answer directly with Cash Flow Strategy rather than fan out. Reserve the full orchestrated fan-out for genuinely multi-domain decisions where cash-flow, tax, debt, and protection interact. Keep each module bounded (its own scope, tools, and Brief) so its internal work stays isolated and only the Brief crosses back — the same reason the SDK returns "only its final message." Avoid over-decomposition: prefer a few well-defined modules over many thin ones.

---

## Summary of net-new guidance for the Manager+specialist design

- Intake produces structured goal objects {horizon, target, priority, constraints, tradeoffs}, generates gap-goals, and logs incomplete-information retrieval tasks; the **priority ranking routes sequencing**, not the client's stated order.
- Each Specialist planning module carries an explicit **Invocation-trigger checklist** and an out-of-scope/escalate boundary; no trigger, no run.
- **Cash Flow Strategy runs first** and its dated baseline is the shared input every later module expresses its effect against (cash flow + reserve adequacy).
- The **Financial Plan Manager alone synthesizes**, netting briefs against goal priority, running an explicit independent-vs-must-pair dependency check, preserving live tradeoffs, and recording decisions with evidence dates.
- **Review state** records the changed-fact conditions that would make a Brief stale; a material event — not a routine sync — re-invokes a module.
- Orchestration is a cost/latency trade (~15× tokens); gate aggressively, answer single-domain questions directly, and keep modules bounded to avoid over-decomposition.
