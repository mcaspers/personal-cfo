# Research: Tax Strategy authoritative sourcing and a recency-safe design pattern

**Date:** 2026-09-12
**Scope:** Product-design research on the *structure of authoritative IRS sourcing* and a *verify-don't-recall* design pattern for the Personal CFO **Tax Strategy & Estimated Payments** specialist planning module. This is **not** a statement of current tax law, **not** a list of current-year rates, thresholds, or limits, and **not** tax, legal, or financial advice. It records which authoritative source *owns* a given determination and how the module should route to it — it deliberately does not restate the substance those sources control. Extends `docs/research/specialist-domains-for-financial-planning.md` (tax module boundary) and the current stub at `plugins/personal-cfo-financial-plan/skills/personal-cfo-tax-strategy/SKILL.md`; do not duplicate the per-module coverage taxonomy under separate authorship.

## Finding

A fact-organizing tax module is safe and durable only if it treats **sourcing as its core competency and figures as always-external**. Two IRS facts anchor the whole design. First, IRS Publications — the plain-language layer the model is most tempted to recall from — are explicitly **not** authoritative: the Internal Revenue Manual states that "Publications are nonbinding on the IRS ... publications should not be cited to sustain a position" ([IRM 4.10.7](https://www.irs.gov/irm/part4/irm_04-010-007)). Second, the authoritative instrument sits above them: the Internal Revenue Bulletin is "the authoritative instrument of the Commissioner of Internal Revenue for announcing official rulings and procedures" ([IRS: taxpayer reliance overview](https://www.irs.gov/newsroom/general-overview-of-taxpayer-reliance-on-guidance-published-in-the-internal-revenue-bulletin-and-faqs)). So the module's job is to route a household situation to the *owning* source, flag pubs as explanatory, and hand the determination to a CPA/EA — never to state the number itself. This aligns the module with the existing **Planning escalation** boundary and the legal gate that "practice before the IRS" includes "giving oral or written tax advice" ([IRS FAQ](https://www.irs.gov/tax-professionals/frequently-asked-questions)).

## Q1. The authoritative IRS source hierarchy

Ordered from most to least authoritative for a fact-organizing tool. The module should always route a determination to the highest applicable layer and mark lower layers as explanatory pointers:

1. **Internal Revenue Code (IRC)** — the statute enacted by Congress (Title 26, U.S. Code). Top authority.
2. **Treasury Regulations (26 CFR)** — Treasury/IRS interpretation of the Code, published in the Federal Register after notice-and-comment; the eCFR carries the current text. The IRS describes regulations as interpreting and directing compliance with the law ([Understanding IRS guidance](https://www.irs.gov/newsroom/understanding-irs-guidance-a-brief-primer)).
3. **Internal Revenue Bulletin (IRB)** — the authoritative channel for **Revenue Rulings** (IRS interpretation of the Code applied to facts), **Revenue Procedures** (official statements of procedure, including annual inflation figures), and **Notices** (substantive interim interpretations). "The authoritative instrument ... for announcing official rulings and procedures" ([reliance overview](https://www.irs.gov/newsroom/general-overview-of-taxpayer-reliance-on-guidance-published-in-the-internal-revenue-bulletin-and-faqs)). Private Letter Rulings and Technical Advice Memoranda are taxpayer-specific and "may not be relied on as precedent."
4. **IRS Publications** — plain-language explanations for taxpayers. **Not authoritative**: "publications should not be cited to sustain a position" ([IRM 4.10.7](https://www.irs.gov/irm/part4/irm_04-010-007)). Excellent as a *map* to the owning Code/Reg/IRB source; never the source of a certified position.
5. **Forms + Instructions** — operational, filing-year-specific; useful to identify *which* line/computation applies, still downstream of the Code/Regs they implement.
6. **Topic / tax-center pages** — navigational entry points (e.g., the gig economy tax center); orientation only.

Design point: the module routes to the **owning** source and flags the pub layer as explanatory, matching the [Understanding IRS guidance](https://www.irs.gov/newsroom/understanding-irs-guidance-a-brief-primer) primer's own framing.

## Q2. Situation → source lever map (verified URLs)

Each URL below was fetched on 2026-09-12 and confirmed to load. These are **durable landing pages** (they change slowly), which is exactly why they are safe to ship locally — unlike the figures inside them. The map tells the module *where to send the household and their CPA/EA*, not what the answer is.

| Household / self-employed situation | Authoritative lever (route here) | Verified URL |
| --- | --- | --- |
| Estimated tax on income without withholding | Form 1040-ES | https://www.irs.gov/forms-pubs/about-form-1040-es |
| Self-employment / sole proprietor income | Schedule C; Schedule SE; Pub 334 | https://www.irs.gov/forms-pubs/about-schedule-c-form-1040 · https://www.irs.gov/forms-pubs/about-schedule-se-form-1040 · https://www.irs.gov/forms-pubs/about-publication-334 |
| Depreciation / business assets, Section 179, bonus | Pub 946 (*How To Depreciate Property*); Form 4562 | https://www.irs.gov/forms-pubs/about-publication-946 · https://www.irs.gov/forms-pubs/about-form-4562 |
| Capital gains & investment income | Schedule D; Pub 550 | https://www.irs.gov/forms-pubs/about-schedule-d-form-1040 · https://www.irs.gov/forms-pubs/about-publication-550 |
| Rental real estate | Schedule E; Pub 527 | https://www.irs.gov/forms-pubs/about-schedule-e-form-1040 · https://www.irs.gov/forms-pubs/about-publication-527 |
| Retirement contributions / distributions | Pub 590-A (contributions); Pub 590-B (distributions) | https://www.irs.gov/forms-pubs/about-publication-590-a · https://www.irs.gov/forms-pubs/about-publication-590-b |
| HSA / tax-favored health accounts | Pub 969 | https://www.irs.gov/forms-pubs/about-publication-969 |
| Equity compensation (RSU/option/ESPP) | Pub 525 (*Taxable and Nontaxable Income*) | https://www.irs.gov/forms-pubs/about-publication-525 |
| Gig / 1099 platform income | Gig economy tax center | https://www.irs.gov/businesses/gig-economy-tax-center |
| Inflation-adjusted annual figures (brackets, standard deduction, contribution and gift/estate limits) | "Inflation-adjusted tax items by tax year" hub + the year's inflation-adjustment news release and its Revenue Procedure | https://www.irs.gov/newsroom/inflation-adjusted-tax-items-by-tax-year |
| Recently legislated changes (OBBBA / "Working Families Tax Cuts") | OBBBA provisions hub | https://www.irs.gov/newsroom/one-big-beautiful-bill-provisions |

Pub titles carry a filing-year in their headers (e.g., "Publication 550 (2025)"), reinforcing that the *page* is durable but its *contents* are dated — the module should ship the page, not the contents.

## Q3. The recency problem — which classes must be verified live, never recalled

Two classes of tax fact go stale fast and must be treated as **live-only**:

- **Annually inflation-adjusted amounts** — bracket thresholds, standard deduction, retirement/HSA contribution limits, and the gift/estate exclusion. These are re-set every year by a Revenue Procedure and summarized in a news release; the IRS maintains a durable index for exactly this reason ([Inflation-adjusted tax items by tax year](https://www.irs.gov/newsroom/inflation-adjusted-tax-items-by-tax-year)). A recalled bracket or limit is a recalled *year*, and therefore wrong by default.
- **Recently legislated changes.** The **One Big Beautiful Bill Act (2025)** ("Working Families Tax Cuts") is the worked example of *why memory is unsafe*: the IRS is standing up implementation across its own newsroom rather than in the (older) publications. Its own hub describes new deductions with IRS-provided "transition relief for tax year 2025" ([OBBBA provisions hub](https://www.irs.gov/newsroom/one-big-beautiful-bill-provisions)). Critically, for depreciation the IRS **points to interim IRB guidance rather than a settled pub**: "Treasury, IRS issue guidance on the additional first year depreciation deduction amended as part of the One, Big, Beautiful Bill," which describes a "100‑percent additional first year depreciation deduction for qualified property" and directs taxpayers to **Notice 2026-11** for current treatment ([IRS newsroom](https://www.irs.gov/newsroom/treasury-irs-issue-guidance-on-the-additional-first-year-depreciation-deduction-amended-as-part-of-the-one-big-beautiful-bill)). This confirms the pattern the product owner needs: the IRS itself routes bonus depreciation / §168(k) and §179 current treatment to a live Notice/Revenue-Procedure layer, above Pub 946. The module must do the same — **point to the source, do not restate a percentage or dollar figure.** Deliverable: these areas are volatile → the skill must verify, not recall.

## Q4. Depreciation as the worked domain (recognize-and-route, not compute)

Depreciation is the clearest domain where the module should **recognize the situation and route it**, never compute, because the determination hinges on structural choices that are fact- and election-specific:

- **Multiple methods** — MACRS as the default cost-recovery system, plus special first-year regimes (bonus / §168(k)) and the §179 election; Pub 946 is titled *How To Depreciate Property* and Form 4562 is *Depreciation and Amortization (Including Information on Listed Property)*, with the form itself carrying the §179 election ([Pub 946](https://www.irs.gov/forms-pubs/about-publication-946) · [Form 4562](https://www.irs.gov/forms-pubs/about-form-4562)).
- **Elections** — §179 expensing and bonus elections are taxpayer choices with dollar and investment limits that are annually adjusted and were changed by OBBBA (see Q3); an election is a *decision*, which belongs to the CPA/EA, not a recalled default.
- **Recapture** — later disposition can convert prior deductions back into income (depreciation recapture), so a first-year deduction is not a standalone fact.
- **Business-use and listed-property tests** — eligibility and method depend on business-use percentage and asset class; "forced" or mixed-use situations are precisely the fact patterns the module should flag for professional determination.
- **Interaction with passive-activity and rental rules** — rental depreciation flows through Schedule E / Pub 527 and can be limited, so depreciation is entangled with other regimes.

Because each of these is an election, a test, or a downstream consequence — not a lookup — the module should build the **asset/event inventory and the questions**, cite Pub 946 / Form 4562 / the OBBBA depreciation Notice as the levers, and escalate the computation. It must not state a current bonus-depreciation percentage as fact.

## Q5. The "verify-don't-recall" design pattern (two platform cases)

The module behaves differently by platform capability, but the *discipline is identical*: organize facts, timeline, and questions; escalate determinations.

**(a) Runtime web/retrieval available.** Before stating **any** figure, fetch-and-verify against the *specific* authoritative IRS URL from the lever map (Q2), and record the **retrieval date** alongside the figure and the source URL. Prefer the IRB Revenue Procedure / Notice over a pub when a figure is inflation-adjusted or recently legislated. If retrieval fails or is ambiguous, fall back to case (b) rather than guessing — a failed fetch is an unresolved item, not a license to recall.

**(b) No runtime web.** **Never** state a figure from memory. Hand the authoritative link to the user and their CPA/EA, mark the item **unresolved**, and capture the fact pattern and the question instead. The Specialist Brief carries the lever URL and the open question, not a number.

In both cases the module produces the organized substrate — a tax-event ledger, a timeline, separated facts/assumptions/unknowns, and named escalation questions — and stops at the determination boundary. This is the direct operational form of the legal gate already in the stub: "practice before the IRS" includes "giving oral or written tax advice" ([IRS FAQ](https://www.irs.gov/tax-professionals/frequently-asked-questions)), so a stated figure or certified position would cross from planning support into representation.

## Q6. What is safe to ship locally vs. what stays a live lever

Ship in the skill (durable, low-staleness):

- **(a) The situation → source lever map** (Q2) — the durable IRS landing URLs change slowly and are the module's routing table.
- **(b) Recency-sensitivity flags** (Q3) — the list of "verify live, never recall" classes (inflation-adjusted amounts; recently legislated / OBBBA changes; depreciation elections and limits).
- **(c) Escalation boundaries** — the Planning escalation list from the stub and `specialist-domains-for-financial-planning.md` (final liability, certified position, filed return, entity/multistate/foreign/estate-gift determinations → CPA/EA/attorney).
- **(d) The verify-don't-recall discipline** (Q5) — the two-case behavior and the retrieval-date requirement.

Never ship (must stay a live lever): any figure, rate, threshold, contribution/exclusion limit, bonus-depreciation percentage, §179 amount, bracket, or one-line "rule summary" that a filing year can change. These are fetched-and-dated (case a) or handed off as an unresolved link (case b) — they are never baked into the skill file.

## Product implication

Concretely, the Tax Strategy specialist planning module should expand from its stub into a **router with a fixed lever table and a recency conscience**, not a calculator. On **Invocation trigger** (self-employment/1099, investment or rental income, equity comp, estimated-payment questions, a large liquidity event, or a new/changed law), it: (1) classifies the household situation and looks up the owning source in the shipped lever map; (2) marks any figure the decision needs against the recency-sensitivity flags; (3) either fetches-and-dates that figure from the specific IRS URL (runtime web) or hands the lever to the user and CPA/EA as an **unresolved** item (no web); (4) returns the shared 6-part **Specialist Brief** — evidence with source dates, facts/assumptions/unknowns kept separate, illustrative scenarios, and named CPA/EA escalation questions — for the Financial Plan Manager alone to fold in. The **Review state** should treat a new law, a new tax year's inflation adjustment, or a new income type as the conditions that make the brief stale — a routine warehouse refresh does not re-invoke it. Depreciation is the flagship recognize-and-route case: inventory the assets and elections, cite Pub 946 / Form 4562 / the OBBBA depreciation Notice, and escalate the computation. The single rule that keeps the module durable and inside "practice before the IRS": **ship the map, never the numbers.**
