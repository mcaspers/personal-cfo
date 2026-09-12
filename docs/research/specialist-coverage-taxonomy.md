# Research: Specialist coverage taxonomy and cross-domain straddle map

**Date:** 2026-09-12  
**Scope:** A per-module recognition checklist — every account, instrument, product, document, and situation each Specialist planning module must catch so nothing is missed — plus the cross-domain "straddle" routing map and the licensed-professional escalation boundary. U.S.-focused, grounded in IRS/DOL/SEC-FINRA/NAIC/CFPB primary sources. This is product-design research, not financial, tax, legal, or insurance advice.

## Finding

The two prior notes settle *which* modules exist and *how* the Manager sequences them; they do not settle *what each module must recognize*. That gap is the real failure mode: a module that names 401(k)/403(b)/HSA but silently omits IRAs, 457(b), pensions, annuities, and cash-value life will confidently miss a household's largest assets. This note extends — does not restate — the taxonomy, shared brief contract, and release order in [specialist-domains-for-financial-planning.md](./specialist-domains-for-financial-planning.md) and the intake/gating/sequencing/synthesis mechanics in [advisor-orchestration-and-specialist-sequencing.md](./advisor-orchestration-and-specialist-sequencing.md). It keeps the CONTEXT.md vocabulary (Specialist planning module, Invocation trigger, Review state, Planning escalation) and adds three product artifacts per module: a **coverage checklist** (the recognition universe), a **straddle map** (items two modules must both catch, and how they route), and a restated **escalation boundary** (the licensed-professional line and its authority).

Two design rules govern the whole document. First, **recognition is not recommendation**: a module must *notice* an annuity or a cash-value policy and record it as a fact even though it must never advise on, sell, or rank the product — the FINRA framing that a financial planner "might have no financial credentials at all" and separately may be a broker, insurance agent, or accountant is exactly why recognition and advice are different jobs. [FINRA: Financial Planners](https://www.finra.org/investors/investing/working-with-investment-professional/financial-planners) Second, **every straddle needs a named owner for each facet** so an item never falls between modules or gets double-counted — a cash-value life policy is a protection instrument *and* a savings balance, and the map below assigns each facet explicitly.

The straddle register (§10) consolidates every cross-module item so the Financial Plan Manager has one routing table.

---

## 1. Cash Flow Strategy

Runs first; its dated baseline is the shared substrate every later module expresses its effect against (see orchestration note §3). Its recognition job is the full inventory of inflows, outflows, and liquidity vehicles — not a budget.

### Coverage checklist

| Group | Must recognize |
| --- | --- |
| Regular income | W-2 wages/salary, hourly, overtime; multiple jobs; pension/annuity income; Social Security; retirement-account distributions |
| Irregular / variable income | Self-employment/1099, gig, freelance; commissions, bonuses, tips; seasonal income; rental income; investment income (interest, dividends, distributions); support payments received |
| Timing structure | Pay cadence (weekly/biweekly/semimonthly/monthly), pay-date drift, employer benefit deductions taken pre-tax at source |
| Recurring fixed outflows | Housing (rent/mortgage/property tax/insurance escrow), utilities, insurance premiums, loan minimums, subscriptions, tuition, childcare, alimony/child support paid |
| Discretionary / variable outflows | Groceries, dining, transport/fuel, travel, shopping; cash & manual spending (per CONTEXT.md) |
| Irregular / seasonal outflows | Annual/semiannual premiums, property tax installments, tuition terms, holidays, quarterly estimated taxes, periodic maintenance |
| Liquidity vehicles | Checking, savings, money-market deposit accounts, CDs, cash-management/brokerage sweep, prepaid/stored value; FDIC/NCUA deposit-insurance status of held cash |
| Buffers & reserves | Emergency/liquidity buffer, sinking funds, unallocated annual cash flow, goal-funding queue |
| Obligated future cash | Estimated tax reserves, insurance deductibles at risk, known lump sums (tax due, tuition, balloon payments) |

CFPB's cash-flow method starts exactly here — tracking "income, resources, and expenses," including everyday spending, bills, and savings. [CFPB: Cash Flow Budget Tool](https://files.consumerfinance.gov/f/documents/cfpb_your-money-your-goals_cash_flow_budget_tool_2018-11_ADA.pdf) The debt-service side of the ledger is measured the way lenders do — debt-to-income is "all your monthly debt payments divided by your gross monthly income." [CFPB: debt-to-income ratio](https://www.consumerfinance.gov/ask-cfpb/what-is-a-debt-to-income-ratio-en-1791/)

### Straddle map

| Item | Co-owning module | Routing |
| --- | --- | --- |
| Loan minimum payments | Debt & Credit | Cash Flow consumes the payment as an outflow; Debt owns payoff/refinance mechanics |
| Estimated-tax reserve, withholding | Tax Strategy | Cash Flow times the cash set-aside; Tax owns the events/amounts |
| Insurance premiums (all lines) | Risk & Insurance | Cash Flow schedules premium outflows; Risk owns coverage adequacy |
| Property tax / homeowners escrow | Property; Risk | Cash Flow carries the outflow; Property owns carrying-cost model; Risk owns the coverage |
| Retirement contributions / distributions | Benefits & Retirement | Cash Flow nets the transfer; Benefits owns limits, match, RMD timing |
| Equity-comp cash events (vest sell, ESPP purchase) | Equity Comp | Cash Flow times the inflow/withholding; Equity owns concentration/tax reserve |

### Scope boundary / escalation

No silent budget creation, no transfer execution, no assertion that a reserve is "adequate," no debt settlement. Escalate imminent inability to pay a critical bill to the servicer and HUD-approved/nonprofit counseling. [CFPB: mortgage options](https://www.consumerfinance.gov/ask-cfpb/if-i-cant-pay-my-mortgage-loan-what-are-my-options-en-268/)

**Product implication.** Invocation trigger: essentially always (first module). Its checklist doubles as the intake completeness gate — any recognized inflow/outflow class with no evidence becomes an incomplete-information retrieval task, not a silent zero.

---

## 2. Tax Strategy & Estimated Payments

Organizes facts and scenarios only. The legal ceiling is hard: the IRS says "practice before the IRS" includes preparing/filing documents and rendering written tax advice, so the module never files, certifies, or represents. [IRS: practice before the IRS](https://www.irs.gov/tax-professionals/frequently-asked-questions)

### Coverage checklist (taxable-event and document universe)

| Group | Must recognize |
| --- | --- |
| Wage/withholding events | W-2 wages, federal/state withholding, Form W-4 status, supplemental-wage withholding on bonuses |
| Self-employment / business | 1099-NEC/1099-K income, Schedule C/SE, self-employment tax, quarterly estimated payments |
| Estimated payments | Form 1040-ES quarterly vouchers; required annual payment / safe-harbor concept; underpayment-penalty exposure |
| Investment events | Interest, dividends (qualified/ordinary), capital gains/losses (short/long), wash sales, tax-loss harvesting facts, 1099-B/DIV/INT, cost-basis records |
| Retirement/tax-advantaged events | Contributions (pre-tax/Roth), employer match, distributions, rollovers/conversions (Roth conversion), RMDs, early-distribution additional tax, QCDs |
| Equity-comp events | ISO/NSO exercise, ESPP purchase/sale, RSU vesting, 83(b) election, AMT exposure, qualified-equity-grant deferral |
| Property/transaction events | Home sale (§121 exclusion), rental income/depreciation, 1099-S, large asset sales, installment sales |
| Life/credit events | Marriage/divorce filing-status change, dependents, education credits, HSA/FSA tax treatment, debt cancellation (1099-C) |
| Documents | Prior-year return, W-2/1099 set, K-1s, 1098 (mortgage/tuition), estimated-payment records, IRS/state notices |
| Situations flagged for escalation | Multistate/nonresident, foreign accounts/FBAR/FATCA, entity structure, estate/gift, material or aggressive positions |

Form 1040-ES is the IRS mechanism for income not subject to withholding and describes a required-annual-payment calculation to avoid underpayment penalties. [IRS: Form 1040-ES](https://www.irs.gov/forms-pubs/about-form-1040-es)

### Straddle map

| Item | Co-owning module | Routing |
| --- | --- | --- |
| Estimated payments / withholding | Cash Flow | Tax owns amount/timing; Cash Flow reserves the cash |
| Roth conversion, RMD, early-distribution tax | Benefits & Retirement | Benefits owns plan mechanics; Tax owns the taxable-event scenario |
| ISO/AMT, RSU/ESPP taxation, 83(b) | Equity Comp | Equity owns the vest/exercise calendar; Tax owns the liability scenario and reserve |
| Home-sale §121, rental depreciation | Property | Property owns carrying-cost/affordability; Tax owns the event treatment |
| HSA/529/ABLE tax treatment | Benefits & Retirement | Benefits owns the account; Tax owns deduction/qualified-distribution facts |
| Owner draws, pass-through K-1, payroll tax | Business-owner Finance | Business owns separation/obligations; Tax owns the events |

### Scope boundary / escalation

Never calculate a final liability, certify a position/deduction, prepare/file, or advise concealment. Escalate entity, equity, multistate, foreign, estate/gift, and material positions to a CPA, EA, or tax attorney. [IRS: practice before the IRS](https://www.irs.gov/tax-professionals/frequently-asked-questions)

**Product implication.** Invocation trigger: any recognized taxable event beyond simple W-2 withholding, or an upcoming estimated-payment date. Output is a tax-event ledger + scenarios + CPA/EA questions — never a return.

---

## 3. Debt & Credit Strategy

Inventory, payoff/refinance alternatives, and cash-flow impact — never negotiation or a specific product direction.

### Coverage checklist

| Group | Must recognize |
| --- | --- |
| Mortgage debt | First mortgage, second/HELOC, home-equity loan; fixed vs. adjustable; escrow; PMI; balloon terms |
| Auto & secured | Auto loans, lease obligations, secured personal loans, title loans |
| Revolving credit | Credit cards, retail cards, HELOC draws, personal lines of credit; fixed vs. variable APR |
| Installment / unsecured | Personal loans, BNPL/point-of-sale installments, medical debt, tax debt/IRS installment agreements |
| Student loans | Federal (subsidized/unsubsidized, PLUS, consolidation), income-driven repayment, forgiveness status; private student loans |
| Business/guaranteed | Personal guarantees on business debt, SBA loans, co-signed obligations |
| Debt attributes | Balance vs. payoff amount, rate/APR, fees, term, minimum payment, delinquency/collections status, secured vs. unsecured |
| Credit facts | Credit reports, credit score factors, utilization, hard inquiries, disputes |

A displayed balance is not a payoff figure — CFPB notes a payoff amount can include interest and fees and "may not be the same as" the current balance. [CFPB: payoff amount](https://www.consumerfinance.gov/ask-cfpb/what-is-a-payoff-amount-and-is-it-the-same-as-my-current-balance-en-205/) APR structure matters: "A fixed-rate APR or fixed APR sets an APR that does not fluctuate with changes to an index." [CFPB: fixed vs. variable APR](https://www.consumerfinance.gov/ask-cfpb/what-is-the-difference-between-a-fixed-apr-and-a-variable-apr-en-45/)

### Straddle map

| Item | Co-owning module | Routing |
| --- | --- | --- |
| Loan minimums / debt service | Cash Flow | Debt owns payoff/refi modeling; Cash Flow carries the outflow and DTI |
| Mortgage / HELOC | Property | Debt owns rate/refi comparison; Property owns total carrying cost & affordability |
| Tax debt / IRS installment agreement | Tax Strategy | Debt owns the payoff schedule; Tax owns the underlying liability |
| 401(k) plan loans | Benefits & Retirement | Benefits owns plan-loan rules; Debt models the repayment as an obligation |
| Business/personally-guaranteed debt | Business-owner Finance | Business owns the obligation calendar; Debt owns household-side payoff impact |
| Cancelled debt (1099-C) | Tax Strategy | Debt owns the settlement facts; Tax owns income treatment |

### Scope boundary / escalation

Do not negotiate or settle debt, direct a specific refinance product, or treat a displayed balance as a payoff. Compare actual Loan Estimates for mortgage offers. [CFPB: compare offers](https://www.consumerfinance.gov/owning-a-home/compare/)

**Product implication.** Invocation trigger: any debt on file, a refinance/payoff question, or a delinquency. Output is a dated debt schedule + scenario table separating balance, payoff quote, rate, fees, payment, timeline.

---

## 4. Benefits & Retirement

The module most prone to missing accounts, so this is the exhaustive one. It recognizes plan/account facts and mechanics; it never selects securities, sets allocation, values holdings, or asserts an outcome is sufficient. DOL distinguishes the two plan families: "A defined benefit plan promises a specified monthly benefit at retirement," while a defined contribution plan "does not promise a specific amount of benefits at retirement." [DOL: types of retirement plans](https://www.dol.gov/general/topic/retirement/typesofplans)

### Coverage checklist — employer defined-contribution plans

| Account | Recognition note & source |
| --- | --- |
| Traditional & Roth 401(k) | Cash-or-deferred DC plan; pre-tax vs. designated Roth. [DOL](https://www.dol.gov/general/topic/retirement/typesofplans) |
| 403(b) / tax-sheltered annuity | "a retirement plan offered by public schools and certain 501(c)(3) tax-exempt organizations." [IRS: 403(b)](https://www.irs.gov/retirement-plans/irc-403b-tax-sheltered-annuity-plans) |
| 457(b) — governmental vs. non-governmental | For "certain state and local governments and non-governmental entities tax exempt under IRC Section 501"; the two branches have distinct rules. [IRS: 457(b)](https://www.irs.gov/retirement-plans/irc-457b-deferred-compensation-plans) |
| TSP / FERS / CSRS | Federal DC (TSP) and federal DB (FERS/CSRS) systems — treat TSP like a 401(k), FERS/CSRS as pension facts |
| Profit-sharing, money-purchase | Employer-funded DC plans; money-purchase has fixed contribution formula |
| SIMPLE 401(k) | Small-employer 401(k) variant |
| ESOP | "a form of defined contribution plan in which the investments are primarily in employer stock." [DOL](https://www.dol.gov/general/topic/retirement/typesofplans) (see Equity Comp straddle) |

### Coverage checklist — IRAs and self-employed plans

| Account | Recognition note & source |
| --- | --- |
| Traditional IRA | "any IRA that isn't a Roth IRA or a SIMPLE IRA." [IRS Pub 590-A](https://www.irs.gov/publications/p590a) |
| Roth IRA | Separate contribution/deduction rules; no owner-lifetime RMD |
| Rollover IRA | Vehicle for employer-plan rollovers; Pub 590-A covers "transfers to and from an IRA" |
| Spousal IRA | Contribution based on working spouse's income. [IRS: IRA contribution limits](https://www.irs.gov/retirement-plans/plan-participant-employee/retirement-topics-ira-contribution-limits) |
| Inherited (beneficiary) IRA | Distinct distribution rules; see Pub 590-B |
| Nondeductible IRA | After-tax basis tracked on Form 8606 |
| SEP-IRA | "allows an employer to make contributions to an employee's traditional SEP IRA or Roth SEP IRA." [IRS Pub 590-A](https://www.irs.gov/publications/p590a) |
| SIMPLE IRA | Small-employer salary-reduction plan. [IRS Pub 560](https://www.irs.gov/publications/p560) |
| Solo / individual 401(k) | Owner-only qualified plan. [IRS Pub 560](https://www.irs.gov/publications/p560) |

### Coverage checklist — pensions, health, education, and hybrid savings

| Account / vehicle | Recognition note & source |
| --- | --- |
| Defined-benefit pension | "promises a specified monthly benefit at retirement." [DOL](https://www.dol.gov/general/topic/retirement/typesofplans) |
| Cash-balance / hybrid DB | DB plan expressed as a hypothetical account balance |
| HSA | Health + retirement savings; "An HSA is 'portable.' It stays with you if you change employers." [IRS Pub 969](https://www.irs.gov/publications/p969) |
| Health FSA & dependent-care FSA | Employer FSAs; use-it-or-lose-it. [IRS Pub 969](https://www.irs.gov/publications/p969) |
| HRA / Archer MSA | Employer-owned reimbursement / older MSA. [IRS Pub 969](https://www.irs.gov/publications/p969) |
| 529 plan | Prepaid-tuition or savings; "a plan operated by a state or educational institution, with tax advantages." [IRS: 529 Q&A](https://www.irs.gov/newsroom/529-plans-questions-and-answers) |
| Coverdell ESA | Education savings account, lower limit than 529 |
| ABLE account | "tax-advantaged savings programs for eligible people with disabilities." [IRS: ABLE](https://www.irs.gov/government-entities/federal-state-local-governments/able-accounts-tax-benefit-for-people-with-disabilities) |
| Nonqualified deferred comp / 409A, SERP, 457(f) | Deferred compensation governed by §409A; audit guide describes the arrangements. [IRS Pub 5528: NQDC guide](https://www.irs.gov/pub/irs-pdf/p5528.pdf) |
| Annuities (fixed/variable/indexed/immediate/deferred/QLAC) | Insurance contracts used for retirement income; variable ones are SEC-registered securities. [Investor.gov: annuities](https://www.investor.gov/introduction-investing/investing-basics/investment-products/annuities) |
| Cash-value life as savings (whole/UL/VUL/IUL) | Recognized as a savings balance/fact; policy mechanics owned by Risk (straddle). [NAIC: life insurance](https://content.naic.org/consumer/life-insurance.htm) |
| Social Security claiming facts | Early at 62 reduces benefit; delayed credits raise it until age 70. [SSA: age reduction](https://www.ssa.gov/benefits/retirement/planner/agereduction.html), [SSA: delayed credits](https://www.ssa.gov/benefits/retirement/planner/delayret.html) |

### Coverage checklist — plan mechanics (must be elicited per account)

Contribution limits and catch-up ("$8,000 if you're age 50 or older" for IRAs) [IRS: IRA limits](https://www.irs.gov/retirement-plans/plan-participant-employee/retirement-topics-ira-contribution-limits); employer match and vesting; eligibility/enrollment; **RMDs** — generally begin at age 73 and apply to traditional IRA/SEP/SIMPLE/401(k)/403(b)/457(b), with the exception that owners are "not required to take withdrawals from Roth IRAs" while alive [IRS: RMDs](https://www.irs.gov/retirement-plans/plan-participant-employee/retirement-topics-required-minimum-distributions-rmds); the pre-59½ 10% additional tax (25% for SIMPLE in first two years) and its exceptions [IRS: exceptions to early-distribution tax](https://www.irs.gov/retirement-plans/plan-participant-employee/retirement-topics-exceptions-to-tax-on-early-distributions); rollovers/conversions; in-service distributions; plan loans and hardship withdrawals; beneficiary designations.

### Straddle map

| Item | Co-owning module | Routing |
| --- | --- | --- |
| HSA | Risk & Insurance; Tax | Benefits owns it as a retirement/health savings account; Risk notes the paired HDHP; Tax owns deduction/qualified-distribution facts |
| Annuities | Risk & Insurance | Benefits recognizes the retirement-income fact; Risk owns policy/suitability mechanics; neither recommends the product |
| Cash-value life | Risk & Insurance; Estate | Benefits records the cash-value savings fact; Risk owns coverage/policy mechanics; Estate owns the death benefit/beneficiary |
| ESOP | Equity Comp | Benefits owns the plan facts; Equity owns the concentration risk |
| Beneficiary designations | Estate & Continuity | Benefits confirms the on-file designation; Estate owns the continuity/estate implication |
| 529 / Coverdell / ABLE | Cash Flow (goal funding); Tax | Benefits owns the account; Cash Flow owns education/goal funding sequence; Tax owns treatment |
| Roth conversion / RMD / plan loan | Tax; Debt | Benefits owns plan mechanics; Tax owns the taxable event; Debt models a plan loan as an obligation |

### Scope boundary / escalation

No security selection, allocation recommendation, trade instruction, valuation, or claim a retirement outcome is sufficient. The SEC describes advisers as giving investment advice about securities under a best-interest duty — route investment recommendations there. [Investor.gov: investment advisers](https://www.investor.gov/introduction-investing/getting-started/working-investment-professional/investment-advisers)

**Product implication.** Invocation trigger: any employer plan, IRA, pension, HSA/education account, annuity, or a contribution/rollover/RMD/claiming question. The checklist is a required-fields inventory: the module must ask "any of these you have?" across all four tables so an unmentioned IRA, pension, or annuity is surfaced, not assumed absent.

---

## 5. Risk, Insurance & Resilience

Coverage/document inventory, gaps, and loss stress-tests — never a policy, limit, insurer, or suitability recommendation. NAIC points consumers to their state insurance department and treats suitability as a state-law analysis of the buyer's finances. [NAIC: annuity suitability & best-interest standard](https://content.naic.org/insurance-topics/annuity-suitability-and-best-interest-standard)

### Coverage checklist (personal lines)

| Line | Must recognize |
| --- | --- |
| Life — term | "Term life insurance is intended to provide lower-cost coverage for a specific period." [NAIC: life](https://content.naic.org/consumer/life-insurance.htm) |
| Life — permanent / cash value | Whole, universal (UL), variable-universal (VUL), indexed-universal (IUL); cash value overlaps savings. [NAIC: life](https://content.naic.org/consumer/life-insurance.htm) |
| Disability | Short-term vs. long-term; "own occupation" vs. "any occupation"; typical ~60% income replacement, elimination period. [NAIC: disability](https://content.naic.org/article/consumer-insight-simplifying-complications-disability-insurance) |
| Health | Employer/marketplace/Medicare/Medicaid; HDHP paired with HSA; deductibles/out-of-pocket max |
| Homeowners / renters / condo | Dwelling, contents, liability; replacement cost; annual review as replacement cost changes. [NAIC: homeowners](https://content.naic.org/consumer/homeowners-insurance.htm) |
| Auto | Liability, collision, comprehensive, UM/UIM; lease/loan coverage requirements |
| Umbrella / excess liability | Above-primary liability; sized to net worth |
| Long-term care | Covers "help with activities of daily living, home care, respite care, hospice care, or adult day care." [NAIC: LTC](https://content.naic.org/consumer/long-term-care-insurance.htm) |
| Flood | Separate from homeowners; NFIP/private |
| Annuities (policy side) | Fixed/variable/indexed/immediate/deferred/QLAC — policy mechanics, surrender, riders (income facet shared with Benefits) |
| Other | Earthquake, valuables/scheduled riders, identity theft, pet; business/professional liability (straddle) |
| Documents | Declarations pages, premium/renewal dates, deductibles, limits, riders, beneficiaries |

### Straddle map

| Item | Co-owning module | Routing |
| --- | --- | --- |
| Cash-value life | Benefits & Retirement; Estate | Risk owns coverage/policy mechanics; Benefits records the cash-value savings fact; Estate owns death benefit/beneficiary |
| Annuities | Benefits & Retirement | Risk owns policy/surrender/suitability; Benefits records the retirement-income fact |
| HDHP + HSA | Benefits & Retirement | Risk owns the health-plan coverage; Benefits owns the HSA account |
| Homeowners / flood premiums | Property; Cash Flow | Risk owns coverage adequacy; Property owns carrying cost; Cash Flow carries the premium |
| Disability / life gap vs. dependents | Estate & Continuity | Risk sizes the protection gap; Estate owns guardianship/continuity documents |
| Professional/business liability | Business-owner Finance | Risk owns the coverage; Business owns the exposure |

### Scope boundary / escalation

No recommendation of a policy, coverage limit, insurer, or a suitability determination; those are state-regulated. Refer to a licensed agent and the state insurance department. [NAIC: consumer](https://content.naic.org/consumer)

**Product implication.** Invocation trigger: a coverage gap signal (dependents, mortgage, business, high net worth), a renewal, or a "what happens if…" loss question. Output is a dated coverage inventory + gap list + loss stress scenarios + agent questions.

---

## 6. Estate & Household Continuity

Document and beneficiary inventory, incapacity/continuity — never drafting, validity opinions, or entity/trust selection.

### Coverage checklist

| Group | Must recognize |
| --- | --- |
| Core directives | Will, revocable living trust, irrevocable trusts (existence only), pour-over will |
| Incapacity | Financial power of attorney, healthcare power of attorney/proxy, advance directive/living will, HIPAA authorization |
| Beneficiary-driven transfers | Retirement-account and life-insurance beneficiary designations, TOD/POD accounts, transfer-on-death deeds |
| Ownership / titling | Joint tenancy WROS, tenancy by entirety, community property, sole ownership |
| Guardianship / dependents | Minor-child guardianship nominations, special-needs trusts, ABLE-account coordination |
| Fiduciary roles | Executor/personal representative, trustee, agent under POA, healthcare agent |
| Continuity records | Asset/account inventory, digital-asset access, password/credential vault, key-contact list, letter of instruction |
| Business continuity | Buy-sell agreement, succession plan, key-person arrangements (straddle) |
| Tax-adjacent | Estate/gift/generation-skipping exposure flags (escalate), prior gifting records |

### Straddle map

| Item | Co-owning module | Routing |
| --- | --- | --- |
| Beneficiary designations | Benefits & Retirement | Benefits confirms the on-file designation; Estate reconciles it with the overall plan |
| Cash-value / term life death benefit | Risk & Insurance | Estate owns beneficiary/estate treatment; Risk owns the policy |
| TOD/POD & account titling | Cash Flow; Benefits | Estate owns transfer mechanism; account modules own the balances |
| Special-needs / ABLE coordination | Benefits & Retirement | Estate owns the trust/guardianship; Benefits owns the ABLE account |
| Business succession / buy-sell | Business-owner Finance | Estate owns continuity documents; Business owns valuation/obligation facts |
| Estate/gift tax exposure | Tax Strategy | Estate flags it; Tax organizes facts; both escalate to attorney/CPA |

### Scope boundary / escalation

Never draft legal documents, opine on validity, advise asset protection/ownership concealment, or choose a trust/entity. Refer all legal/estate choices to a licensed attorney in the relevant state.

**Product implication.** Invocation trigger: no will/directive on file, a minor dependent, unknown beneficiaries, a business, or a life event (marriage/birth/death). Output is a dated document inventory + missing-item list + attorney-briefing checklist.

---

## 7. Equity Compensation (conditional)

RSU/options/ESPP/ESOP/private equity event calendar and concentration/liquidity/tax-reserve facts — never a hold/sell/exercise/diversify recommendation or basis determination.

### Coverage checklist

| Instrument | Must recognize (source-dated plan terms) |
| --- | --- |
| RSUs / RSAs | Grant, vesting schedule, vest-date FMV, sell-to-cover withholding |
| Non-qualified stock options (NSOs) | Grant/strike, vest, exercise window, spread taxed as ordinary income at exercise. [IRS Pub 525](https://www.irs.gov/publications/p525) |
| Incentive stock options (ISOs) | Statutory options; no ordinary income at exercise if holding met, but AMT preference. [IRS Pub 525](https://www.irs.gov/publications/p525) |
| ESPP | Statutory purchase plan; discount, lookback, qualifying vs. disqualifying disposition |
| ESOP | DC plan holding employer stock — plan facts shared with Benefits. [DOL](https://www.dol.gov/general/topic/retirement/typesofplans) |
| Private-company equity | Founder shares, private RSUs, profits interests, 83(b) elections, SAFEs, secondary/tender events |
| Qualified equity grants | Up to 5-year income-tax deferral election for eligible employees. [IRS Pub 525](https://www.irs.gov/publications/p525) |
| Cross-cutting facts | Vesting cliffs, blackout/trading windows, 10b5-1 plans, lockups, concentration % of net worth, expiration dates |

### Straddle map

| Item | Co-owning module | Routing |
| --- | --- | --- |
| ISO/AMT, RSU/ESPP taxation, 83(b) | Tax Strategy | Equity owns the event calendar; Tax owns the liability/reserve scenario |
| Vest-sale proceeds, ESPP purchase cash | Cash Flow | Equity owns timing/withholding; Cash Flow nets the inflow/outflow |
| ESOP | Benefits & Retirement | Equity owns concentration; Benefits owns plan mechanics |
| Concentration vs. diversification need | (escalate) | Equity states the concentration fact; a licensed investment professional owns any diversification advice |

### Scope boundary / escalation

Do not advise whether to exercise, hold, sell, or diversify, and do not determine basis or tax treatment. IRS treats employer stock as fact-specific income/tax topics. [IRS Pub 525](https://www.irs.gov/publications/p525)

**Product implication.** Invocation trigger: any grant/vest/exercise/ESPP/ESOP fact or an upcoming vest/expiration. Output is an event timeline + concentration fact + tax-reserve scenario feeding Cash Flow and Tax.

---

## 8. Property & Major Purchases (conditional)

Home/vehicle carrying costs and affordability scenarios — never an appraisal or a mortgage/loan-product recommendation.

### Coverage checklist (carrying-cost components)

| Component | Must recognize |
| --- | --- |
| Financing | Purchase price, down payment, mortgage/auto loan terms, rate, PMI, points, closing costs |
| Recurring ownership | Property tax, homeowners/condo/flood insurance, HOA/condo fees, utilities |
| Maintenance & reserves | Routine maintenance, repair sinking fund, major-system replacement reserve |
| Vehicle-specific | Registration, insurance, fuel/charging, maintenance, depreciation, lease-vs-buy terms |
| Transaction readiness | Loan Estimates, inspection, appraisal (as a document, not an opinion), title/escrow |
| Affordability inputs | DTI, reserve after down payment, effect on other goals |

CFPB's guidance is to compare actual Loan Estimates from multiple lenders rather than accept one offer. [CFPB: compare offers](https://www.consumerfinance.gov/owning-a-home/compare/)

### Straddle map

| Item | Co-owning module | Routing |
| --- | --- | --- |
| Mortgage / HELOC / auto loan | Debt & Credit | Property owns total carrying cost; Debt owns rate/refi comparison |
| Property tax / homeowners / flood | Cash Flow; Risk | Property owns the carrying model; Cash Flow carries the outflow; Risk owns coverage |
| Home-sale §121, rental depreciation | Tax Strategy | Property owns the transaction; Tax owns event treatment |
| Down payment vs. reserve/goals | Cash Flow | Property owns affordability; Cash Flow owns liquidity/goal tradeoff |

### Scope boundary / escalation

No appraisal or mortgage/loan-product recommendation; compare Loan Estimates and refer to lender/CPA/attorney as applicable. [CFPB: compare offers](https://www.consumerfinance.gov/owning-a-home/compare/)

**Product implication.** Invocation trigger: a contemplated home/vehicle purchase, refinance, or a carrying-cost question. Output is an evidence-based carrying-cost scenario + goal tradeoff + decision checklist.

---

## 9. Business-owner Finance (conditional)

Separate household and business cash flow; owner-pay, tax-reserve, debt-guarantee, and benefit/retirement-plan facts — never entity formation, tax conclusions, valuation, payroll, or transaction advice.

### Coverage checklist

| Group | Must recognize |
| --- | --- |
| Entity & structure (facts only) | Sole prop, partnership/LLC, S-corp, C-corp; ownership %, K-1 vs. W-2 owner pay |
| Owner compensation | Owner draws/distributions, reasonable-comp salary, guaranteed payments, distributions timing |
| Business cash flow | Revenue seasonality, receivables/payables, operating reserve, commingling risk vs. household |
| Tax obligations | Estimated payments, payroll tax deposits, sales/use tax, 1099 filing obligations (escalate treatment) |
| Business debt | Term loans, lines of credit, SBA loans, personal guarantees, equipment financing |
| Benefits/retirement plans | SEP-IRA, SIMPLE IRA, solo/individual 401(k), defined-benefit/cash-balance owner plans (shared with Benefits). [IRS Pub 560](https://www.irs.gov/publications/p560) |
| Risk/continuity | Business/professional liability, key-person, buy-sell, succession, business-interruption coverage |
| Documents | Operating agreement, prior business returns, payroll records, financial statements |

### Straddle map

| Item | Co-owning module | Routing |
| --- | --- | --- |
| Owner draws / K-1 / payroll tax | Tax Strategy; Cash Flow | Business owns separation & owner-pay; Tax owns events; Cash Flow nets household inflow |
| SEP/SIMPLE/solo-401k/DB owner plans | Benefits & Retirement | Business flags the plan exists; Benefits owns contribution/vesting mechanics |
| Personally-guaranteed business debt | Debt & Credit | Business owns the obligation; Debt owns household-side payoff impact |
| Buy-sell / succession | Estate & Continuity | Business owns valuation/obligation facts; Estate owns continuity documents |
| Business/professional liability, business interruption | Risk & Insurance | Business owns the exposure; Risk owns the coverage |

### Scope boundary / escalation

No entity formation, tax conclusion, valuation, payroll, or transaction advice. Escalate to a CPA/EA, business attorney, and where applicable a valuation/transaction professional.

**Product implication.** Invocation trigger: any business income/entity fact, commingled accounts, or an owner-pay/tax-reserve question. Output is a linked-but-separate cash-flow view + obligation calendar + CPA/attorney questions.

---

## 10. Consolidated straddle register

One routing table so no cross-module item falls between modules or is double-counted. "Owns facet" is the single accountable module per facet; "also catches" modules must recognize the item and hand off.

| Straddle item | Owns facet (module → facet) | Also catches |
| --- | --- | --- |
| Cash-value life (whole/UL/VUL/IUL) | Risk → policy/coverage mechanics; Benefits → cash-value savings fact; Estate → death benefit/beneficiary | Cash Flow (premium), Tax (treatment) |
| Annuities (fixed/variable/indexed/immediate/deferred/QLAC) | Risk → policy/surrender/suitability; Benefits → retirement-income fact | Cash Flow (income/premium), Tax (event) |
| HSA | Benefits → account/retirement savings; Risk → paired HDHP | Tax (deduction), Cash Flow (contribution) |
| ESOP | Benefits → plan mechanics; Equity → concentration | Tax (distribution), Estate (beneficiary) |
| Beneficiary designations | Estate → estate/continuity effect; Benefits → on-file confirmation | Risk (life policies) |
| 529 / Coverdell / ABLE | Benefits → account; Cash Flow → education/goal funding | Tax (qualified distributions) |
| Property tax & homeowners/flood insurance | Property → carrying-cost model; Risk → coverage adequacy | Cash Flow (outflow) |
| Mortgage / HELOC | Debt → rate/refi comparison; Property → total carrying cost | Cash Flow (payment/DTI) |
| Equity-comp taxation (ISO/AMT, RSU, ESPP, 83(b)) | Equity → event calendar; Tax → liability/reserve | Cash Flow (proceeds/withholding) |
| Estimated payments / withholding | Tax → amount/timing; Cash Flow → cash reserve | — |
| 401(k) plan loan | Benefits → plan-loan rules; Debt → repayment obligation | Cash Flow (payment) |
| Owner pay / K-1 / payroll tax | Business → separation & owner-pay; Tax → events | Cash Flow (household inflow) |
| Business/personally-guaranteed debt | Business → obligation calendar; Debt → household payoff impact | Cash Flow (payment) |
| Buy-sell / business succession | Business → valuation/obligation facts; Estate → continuity documents | Risk (key-person) |
| Owner retirement plans (SEP/SIMPLE/solo-401k/DB) | Benefits → contribution/vesting mechanics; Business → plan exists | Tax (deduction) |

**Product implication.** The Financial Plan Manager loads this register as its routing law: when any listed item is recognized by one module, the Manager confirms the "owns facet" module holds each facet and that "also catches" modules received the handoff — the operational form of the orchestration note's "independent vs. must-pair" dependency check. A recognized straddle with an unrouted facet is a plan gap, logged like an incomplete-information task, not a silent omission.
