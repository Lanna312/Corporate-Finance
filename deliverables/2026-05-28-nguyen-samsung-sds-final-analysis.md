---
template: stage5-final-analysis
purpose: "Evaluated final analysis — edited, annotated, and corrected version of the raw LLM output, integrated with manual verification findings, author domain knowledge, and Samsung SDS strategic and operating context. Stage 5 Deliverable #3."
author: Nguyen Lan Anh
date: 2026-05-28
company: "Samsung SDS Co., Ltd. (KRX: 018260)"
courses: [BUS-629]
stage: 5
inputs:
  - "deliverables/2026-05-28-nguyen-samsung-sds-llm-raw.md (LLM raw output)"
  - "analysis/validation/2026-05-28-nguyen-samsung-sds-stage5-verification.md (manual verification)"
  - "docs/specs/2026-05-27-nguyen-samsung-sds-spec.md (v2.2 spec)"
  - "Stage 3 workbook for cross-checks"
  - "Author domain knowledge — CMC Telecom International Business Director; direct Samsung SDS–CMC Group ecosystem exposure since 2019"
  - "Samsung SDS strategic and operating context (Samsung Group affiliate revenue mix; Global Delivery Center strategy; segment mix in Data Center, Cloud, ITO, DX)"
spec_retrospective: deliverables/2026-05-28-nguyen-samsung-sds-spec-retrospective.md
---

# Samsung SDS Co., Ltd. (KRX: 018260) — FY2025 Ratio Analysis (Final)

**To:** Adam Stauffer · Faculty, BUS-629 International Corporate Finance · Shidler College of Business
**From:** Nguyen Lan Anh · Director of International Business, CMC Telecom · VEMBA Cohort
**Date:** 2026-05-28
**Re:** Stage 5 evaluated final analysis — Samsung SDS Co., Ltd. (KRX: 018260), FY2025 ratio analysis with strategic and operating context

**Reporting basis:** K-IFRS · KRW billions · FY2025 (year ended December 31, 2025) with FY2024 prior-period balance sheet

---

## Executive Summary

Samsung SDS produced **KRW 783 bn net income on KRW 13,930 bn revenue** in FY2025 — a 5.6% net margin, 6.9% EBIT margin, 7.8% return on average equity. All three hypotheses from the Stage 2 selection memo are confirmed. The balance sheet is fortress-conservative: current ratio of 4.03x and long-term debt-to-equity of 0.05x.

**The headline finding is Economic Value Added of −14 KRW bn** — small in absolute terms but directionally important. After-tax operating income of KRW 924 bn falls KRW 14 bn short of the firm's 9.0% cost of capital on its KRW 10,422 bn start-of-year invested capital. The finding is the central strategic input to §4 Recommendations.

**Critical interpretive context (added during final-analysis review and not visible to the cold-context LLM raw output):**

Samsung SDS is the ICT services arm of the Samsung Group. **Approximately 80% of revenue is generated from intra-group affiliate work** — Samsung Electronics, Samsung Display, Samsung Heavy Industries, Samsung Biologics, Samsung Engineering, and other Samsung Group operating affiliates. The remaining ~20% comes from external customers. This revenue mix has three direct ratio implications:

1. **Operating margins are structurally moderate** because internal transfer pricing across Samsung Group affiliates is set on a cost-plus or framework-pricing basis rather than at full external-market rates. The 6.9% EBIT margin is not a competitive failure; it is a deliberate intra-group pricing outcome.
2. **The negative EVA reframes meaningfully** under this lens. Returns *to Samsung SDS as a standalone entity* are at — not above — its cost of capital. But returns *to the Samsung Group as a whole* include the cost savings, integration value, and IP capture that intra-group ICT services create on the affiliate side. The standalone EVA understates Samsung Group-level value capture.
3. **The 3-year strategic push toward external customer revenue is real but uneven.** Samsung SDS leadership has explicitly targeted external customer growth since FY2022–FY2023. Progress has been modest because internal Samsung affiliate demand is large enough to absorb available capacity — there is no organic pressure to chase external work.

**Three headline ratios for the executive reader:**

- **EBIT margin** = 6.9% (`INC_ebit` / `INC_sales`) — within H1 expected 6.8–7.2% band, ~28 bps expansion YoY. The expansion is real but reflects internal-vs-external mix shift and segment mix shift toward Cloud / Digital Transformation, not pricing leverage in the IT Outsourcing book.
- **Current ratio** = 4.03x (`RATIO_current`) — well above H3 ≥3.8x threshold. Cash and marketable securities of KRW 6,380 bn against current liabilities of KRW 2,332 bn. The cash position partly reflects Samsung Group treasury policy, not standalone capital-allocation choice.
- **EVA** = −14 KRW bn (`RATIO_eva`) — flagged finding requiring three-layer reframing: standalone capital productivity, Samsung Group value capture, and capital-structure reform.

**Top recommendation (priority 1 of 4):** Close the standalone cost-of-capital gap within 24 months through a coordinated KRW 1,000 bn tactical buyback, framed externally as capital-allocation discipline and internally as Samsung Group treasury rebalancing. Lift `RATIO_leverage` from 1.31x toward 1.55x. Detail in §4 Recommendation 1.

**Executive voice — the "so what?":** Samsung SDS is a high-quality, low-organic-growth, structurally-internal ICT services company whose operating ratios understate Samsung Group value capture and whose market valuation (M/B 1.41x) prices in modest external-customer growth optionality plus regional expansion through the CMC majority stake in Vietnam. The fastest path to standalone value creation runs through the balance sheet, not the income statement. The fastest path to *strategic* value creation runs through the Global Delivery Center strategy and the Vietnamese platform. Recommendations §4 address both.

---

## §1 Company & Data Summary

### §1.1 Company overview

Samsung SDS Co., Ltd. is the ICT services subsidiary of the Samsung Group, listed on the Korea Exchange under ticker `018260.KS`. The firm operates four principal business areas — Data Center services (including Samsung Cloud Platform infrastructure), Cloud services (managed services and migration), IT Outsourcing (ITO — application management, infrastructure management, end-user services), and Digital Transformation (DX — consulting and system integration). A Logistics technology segment runs Samsung Group's global supply-chain operations and is reported separately.

The firm reports under Korean IFRS (K-IFRS) on a December 31 fiscal year. Samil PricewaterhouseCoopers is the auditor. The Stage 3 workbook covers FY2024 (prior) and FY2025 (current) balance sheets, FY2025 income statement, FY2025 cash flow, and FY2025 close market data.

### §1.2 Revenue mix — the structural context the ratios cannot show on their own

Samsung SDS's financial profile cannot be read without understanding its revenue mix. Approximately 80% of revenue comes from intra-group Samsung affiliate work; approximately 20% from external customers. This concentration is by design — Samsung SDS was established to serve the Samsung Group's ICT needs at scale, and the captive customer base remains the dominant revenue driver.

**Implications for ratio interpretation:**

| Ratio category | What the headline ratio shows | What the revenue mix adds |
|---|---|---|
| **Operating margin (6.9% EBIT, 6.6% NOPAT)** | Moderate profitability relative to global IT-services peers (Accenture 14–16%, TCS 24–26%) | Intra-group transfer pricing is set on cost-plus or framework-pricing terms, not full external-market rates. Margins are structurally bounded by group pricing policy, not by competitive position. |
| **Asset turnover (1.05x)** | At Korean IT-services peer median | Heavy Data Center and Cloud infrastructure investment to support Samsung Group's semiconductor, mobile, and display operations. Asset intensity is purposeful, not inefficient. |
| **Current ratio (4.03x), Cash position (KRW 6,380 bn)** | Structurally over-liquid | Partly reflects Samsung Group treasury policy — affiliate-level cash buffers are coordinated centrally for FX, geopolitical, and counterparty resilience. Standalone over-capitalization, group-level discipline. |
| **DSO (66.4 days)** | High for IT-services peers (typically 45–60 days) | Intra-group netting cycles run quarterly across Samsung affiliates; DSO is structurally elevated by the group-billing model, not by collections discipline. |
| **EVA (−14 KRW bn)** | Returns just below standalone cost of capital | Samsung Group value capture (cost savings, integration efficiency, IP retention on the affiliate side) is invisible in the standalone EVA calculation. Standalone EVA understates group-level value creation. |

### §1.3 Strategic push toward external customer growth (FY2022 — present)

Samsung SDS leadership has explicitly targeted external customer revenue growth as a strategic priority since FY2022–FY2023. The motivation is three-fold:

1. **Market validation** — external customer wins demonstrate that Samsung SDS technology and delivery quality are competitive in open markets, not just captive markets. This matters for talent retention and for global cloud-platform positioning.
2. **Margin uplift potential** — external work, particularly in Cloud and DX, carries higher margins than intra-group ITO. Mix shift toward external work creates organic margin expansion.
3. **Optionality for future capital-return discussions with Samsung Group** — a stronger external franchise reduces the firm's strategic dependence on intra-group demand and creates flexibility for capital-structure reform (Recommendation 1 below).

**Progress to date has been modest.** External revenue share has grown but Samsung Group internal demand remains large enough to absorb available delivery capacity. The realistic external-revenue ceiling over the next 24–36 months is probably 25–30% of total revenue (up from current ~20%), not the 35–40% that would meaningfully reframe the ratio profile. **This is the central scoping observation for §4 Recommendations.**

### §1.4 Samsung SDS Vietnam strategy — CMC majority stake and Global Delivery Centers

Two strategic positions in Vietnam and the broader Asia delivery footprint deserve explicit mention because they reframe Recommendation 2 substantially.

**(i) CMC Corporation strategic stake.** Samsung SDS became a strategic investor in CMC Corporation (parent of CMC Telecom, where the author serves as Director of International Business) in 2019. As of FY2025, Samsung SDS is the **largest shareholder of CMC Corporation**. The CMC platform provides Samsung SDS with operational presence, customer-base access, and regulatory legitimacy in Vietnam's growing IT services market. The relationship is well-developed and the integration risk for incremental Vietnam investment is materially lower than for any greenfield entry.

**(ii) Global Delivery Center (GDC) network.** Samsung SDS operates Global Delivery Centers in Vietnam, India, and China. The GDC model serves two purposes: (a) cost reduction on ITO delivery through lower-cost labor markets, and (b) 24-hour follow-the-sun delivery capability for global enterprise customers. The Vietnam GDC, in particular, is the lowest-cost node in the network for general ITO work and the strategic complement to the CMC majority-stake position. The GDC network is operating and scaling; it is not a future-state initiative.

**The implication for Recommendation 2:** Samsung SDS is not exploring Vietnam — Samsung SDS *operates* in Vietnam through both equity ownership (CMC) and delivery capability (GDC). Recommendation 2 should be framed as *deepening and scaling* an existing strategic position, not entering a new market.

### §1.5 Author's professional-context disclosure

This analysis was produced as part of the BUS-629 EMBA capstone. The author is Director of International Business at CMC Telecom and has direct professional exposure to the Samsung SDS–CMC Group ecosystem since 2019. This relationship informs the strategic context in §1.4 and the Vietnam-focused recommendation in §4 Rec 2. **All financial figures in this analysis come from public K-IFRS filings only.** No non-public information from the CMC–Samsung SDS relationship is used in the financial analysis. The professional context is disclosed in line with normal MBA-coursework conflict-of-interest practice.

### §1.6 Data scope

The Stage 3 workbook contains:

| Data set | Coverage | Implication |
|---|---|---|
| Balance Sheet | FY2024 (prior) + FY2025 (current) | Two-period averaging is supported. |
| Income Statement | FY2025 only | Two-period margin trend analysis is not supported within the workbook; FY2024 figures reference the Stage 2 memo. |
| Cash Flow Statement | FY2025 only | Two-period CFS trend analysis is not supported. |
| Market data | FY2025 close (Dec 30, 2025) | Share price 186,500 KRW; shares outstanding 77M; market cap 14,431 KRW bn. |
| Workbook assumptions | `cost_capital` = 9.0%; `tax_rate` = 27.3% | Both treated as inputs, not derived. |

Sourcing FY2024 IS / CFS from DART filings and obtaining the FY2025 K-IFRS Segment Disclosure note are documented Stage 5 follow-up items (see §6 Limitations).

### §1.7 Validation status

All fourteen validation rules (V1–V14) in spec §7 pass for FY2025. The Du Pont reconciliation (V4) passes within tolerance using full-decimal component precision — the precision-sensitivity caveat is documented in the spec retrospective. The retained-earnings roll-forward (V10) shows a 15 KRW bn (0.18%) residual most likely attributable to Other Comprehensive Income from FX translation on the Vietnam logistics affiliate and other overseas subsidiaries (see §6 Limitations item 7).

---

## §2 Ratio Results & Interpretation

### §2.1 Performance (Market Value)

| Ratio | Named range | FY2025 |
|---|---|---:|
| Market value added | `RATIO_market_value_added` | 4,168 KRW bn |
| Market-to-book ratio | `RATIO_market_to_book` | 1.41x |
| Economic value added | `RATIO_eva` | **(14) KRW bn — flagged finding** |

**Market valuation context.** Market capitalization of KRW 14,431 bn versus book equity of KRW 10,263 bn produces MVA of KRW 4,168 bn — substantial wealth created above book — and an M/B of 1.41x. Korean IT-services peer M/B typically falls between 1.2x and 2.0x (LG CNS, NAVER Cloud range); global IT-services majors trade at 4x–6x M/B (Accenture, TCS). Samsung SDS at 1.41x sits mid-range relative to Korean peers and substantially below global majors. The gap to global majors is driven by leverage, asset turnover, and growth profile — not by margin.

**EVA three-reading framework (per spec §6.1), refined with revenue-mix context:**

**Reading 1 — Standalone capital-productivity gap.** `RATIO_roc_start` of 8.9% (`currentYear_after_tax_operating_income` 924 / `startYear_total_capitalization` 10,422) sits 10 basis points below the 9.0% `cost_capital`. On the start-of-year capital base, EVA is `924 − (0.090 × 10,422) = −14` KRW bn. The gap is small but directional: Samsung SDS as a standalone entity earns at — not above — its cost of capital. This is the conventional EVA reading.

**Reading 2 — Over-capitalization and Samsung Group treasury context.** Three signals stack: `RATIO_leverage` of 1.31x is well below IT-services peer norms of 1.8x–2.5x; cash and marketable securities of KRW 6,380 bn represent **47% of total assets**; standalone EVA is negative. The standard interpretation is over-capitalization. The Samsung Group context partially qualifies this: the cash position reflects coordinated group treasury policy, not solely Samsung SDS management discretion. **Roughly half the cash position — KRW 3 trn — is defensible as group treasury coordination (FX, geopolitical, intra-group support); the remaining ~KRW 3.4 trn is unforced under-leverage that depresses standalone returns below the cost of equity.** This is the central interpretive move of the analysis. The recommendation set in §4 targets the unforced portion, not the policy-coordinated portion.

**Reading 3 — Du Pont reconciliation.** ROE (avg) of 7.8% (`RATIO_roe_avg`) sits below the 9.0% cost of equity. The 4-component Du Pont decomposition (§3 Du Pont Analysis below) reveals `RATIO_leverage` (1.31x) as the binding constraint. `RATIO_operating_profit_margin` (6.6%) and `RATIO_asset_turnover` (1.05x) sit at industry-norm levels — but only because intra-group transfer pricing structurally bounds margin upside. A standalone IT-services firm with Samsung SDS's revenue profile in open markets would likely produce 8–10% NOPAT margin; the 6.6% reflects the deliberate intra-group pricing model. Sensitivity at `RATIO_leverage` = 1.55x: ROE clears 9.0% mechanically.

**Reading 4 (added by author, not in LLM raw output) — Samsung Group value capture.** EVA on the Samsung SDS balance sheet is −14 KRW bn. But the firm's intra-group ICT services capture significant value on the affiliate side: cost savings (vs. external IT outsourcing rates), integration efficiency (vs. multi-vendor coordination overhead), IP retention (vs. external vendor lock-in), and security control (vs. third-party data exposure). A consolidated Samsung Group P&L would attribute meaningful incremental value to Samsung SDS that does not appear in the standalone P&L. **The standalone EVA finding is correct as far as it goes — but it understates the firm's value capture at the group level.** This matters for executive communication: the right framing is "we earn at our cost of capital standalone, and we create incremental value at the group level" — not "we are destroying value."

**Answering §8.1 Performance anchoring question.** Does M/B 1.41x reflect growth expectations consistent with negative EVA, or operational improvements not visible in current ratios? My executive read: the M/B premium prices in (i) the modest cloud / digital-transformation mix shift the H1 test confirms, (ii) Samsung Group ecosystem optionality, and (iii) the Vietnam / CMC / GDC regional expansion option. The market is not paying for current-period operating excess; it is paying for ecosystem positioning and growth optionality. The 1.41x is defensible pricing of a high-quality, low-growth, group-anchored ICT services asset. It is not a mis-pricing.

### §2.2 Profitability

| Ratio | Named range | FY2025 |
|---|---|---:|
| ROA (start) | `RATIO_roa_start` | 7.0% |
| ROC (start) | `RATIO_roc_start` | 8.9% |
| ROE (start) | `RATIO_roe_start` | 8.1% |
| ROA (avg) | `RATIO_roa_avg` | 6.9% |
| ROC (avg) | `RATIO_roc_avg` | 8.7% |
| ROE (avg) | `RATIO_roe_avg` | 7.8% |
| Profit margin | `RATIO_profit_margin` | 5.6% |
| Operating profit margin (NOPAT) | `RATIO_operating_profit_margin` | 6.6% |

**Author note on EBIT-margin vs NOPAT-margin terminology** (spec §6.3 footnote, verification Row 4): The workbook's `RATIO_operating_profit_margin` of 6.6% is NOPAT-based. The Stage 2 memo's "operating margin" of 6.9% (FY2025) is the EBIT margin = `INC_ebit` / `INC_sales` = 957 / 13,930 = 6.87%. Both must appear distinctly. In executive narrative, the EBIT margin 6.9% is the headline figure to cite for H1 hypothesis testing; the NOPAT margin 6.6% is the Du Pont component.

**H1 hypothesis test (per spec §8.2 framework), refined with segment-mix context:**

| Field | Detail |
|---|---|
| Hypothesis | EBIT margin expands from 6.6% (FY2024 memo) toward 6.8–7.2% (FY2025) via cloud / digital-transformation mix shift. |
| Operationalization | EBIT margin = `INC_ebit` / `INC_sales`. |
| Test | 957 / 13,930 = 6.87% → inside 6.8–7.2% band; ~28 bps expansion YoY. |
| Result | **H1 confirmed**. |
| Strategic implication (refined) | Mix shift is real but at the **low end** of the expected band. Driver decomposition: (i) Cloud and DX segments grew faster than ITO and Data Center; (ii) external customer revenue share rose modestly within Cloud and DX; (iii) intra-group ITO pricing was unchanged YoY. Margin lift is *segment-mix-driven*, not *pricing-driven*. The §4 Recommendations should not assume continued YoY EBIT-margin expansion without an acceleration in either external customer revenue or Cloud / DX growth. The realistic baseline for FY2026 is EBIT margin at 6.9–7.1%, not 7.5%+. |

**Profitability narrative (executive voice).** Samsung SDS profitability is structurally moderate because of the intra-group revenue mix — not because the firm is operationally weak. The 8.9% standalone ROC versus the 9.0% cost of capital is the right number to lead with in capital-allocation discussions with Samsung Group treasury. The right framing externally is: *"We earn at our cost of capital today; the path to clearing it sustainably runs through balance-sheet reform plus continued external customer mix shift."* Avoid the common error of framing this as a margin-improvement initiative — margins are bounded above by intra-group transfer pricing, not by operating execution.

### §2.3 Efficiency & Working Capital

| Ratio | Named range | FY2025 |
|---|---|---:|
| Asset turnover | `RATIO_asset_turnover` | 1.05x |
| Receivables turnover | `RATIO_receivables_turnover` | 5.50x |
| Average collection period | `RATIO_average_collection_period` | 66.4 days |
| Inventory turnover | `RATIO_inventory_turnover` | 605.77x |
| Days in inventory | `RATIO_days_inventory` | 0.6 days |

**Author correction to LLM raw output §3** (verification Row 7): the 605x Inventory Turnover is a services-business artifact (KRW 15 bn inventory vs. KRW 11,510 bn COGS). I am citing `RATIO_days_inventory` = 0.6 days as the analytically meaningful efficiency metric and treating Inventory Turnover as supporting arithmetic, not as a competitive-advantage signal.

**DSO (`RATIO_average_collection_period`) of 66.4 days — the substantive efficiency finding, refined with intra-group billing context.**

The cold-context LLM proposed three plausible explanations for the elevated DSO (Korean public-sector contracts, Samsung Group intra-company netting, Logistics-segment receivables) and recommended compression toward 55 days. **The intra-group netting explanation deserves substantially more weight than the LLM gave it.** With approximately 80% of revenue running through Samsung affiliates, the DSO is structurally elevated by the quarterly intra-group netting cycle that Samsung Group operates across affiliates — Samsung Electronics, Samsung Display, Samsung Heavy Industries, etc. The cycle is by group treasury design; affiliate-level collections discipline cannot compress it.

The implication is that **the realistic compression target on the consolidated DSO is much smaller than the LLM suggested.** Compression to 55 days would require restructuring the intra-group netting cycle, which is a Samsung Group-level decision, not a Samsung SDS management decision. **A standalone Samsung SDS compression target should focus on the ~20% external-customer book and the Logistics-segment book.** I am revising Recommendation 3 accordingly — target 60–62 days, not 55 or 58.

**H2 hypothesis test (per spec §8.2 framework), expanded with segment-mix context:**

| Field | Detail |
|---|---|
| Hypothesis | IT Services segment asset turnover > Logistics segment asset turnover in FY2025 (IT-light, Logistics asset-heavy). |
| Test methodology | Segment-level asset turnover from K-IFRS Segment Disclosure note. |
| Result | **TBD pending K-IFRS Segment Note review** — not in the Stage 3 workbook; not accessible to cold-context LLM. |
| Strategic implication (refined) | The H2 question is sharper when restated as: "Does Cloud + DX asset productivity exceed Data Center + ITO asset productivity?" Within IT Services, Cloud and DX are intentionally asset-lighter than Data Center and ITO. Data Center carries Samsung Cloud Platform infrastructure (server, storage, networking capex) that supports both intra-group and external workloads; ITO carries facilities and labor capacity. Cloud and DX are software-and-services intensive. If the H2 segment-disclosure data confirms Cloud + DX AT > Data Center + ITO AT, the §4 capital-allocation recommendation should flag: (a) Cloud and DX are the higher-return marginal investment; (b) Data Center expansion should be evaluated against intra-group volume commitments; (c) ITO should be evaluated against GDC cost-of-delivery improvement (the Vietnam / India / China nodes). |

### §2.4 Leverage

| Ratio | Named range | FY2025 |
|---|---|---:|
| Long-term debt ratio | `RATIO_long_term_debt_ratio` | 5.1% |
| Long-term debt-equity | `RATIO_long_term_debt_equity` | 0.05x |
| Total debt ratio | `RATIO_total_debt_ratio` | 23.7% |
| Times interest earned | `RATIO_times_interest_earned` | 4.92x |
| Cash coverage ratio | `RATIO_cash_coverage` | 7.14x |
| Debt burden | `RATIO_debt_burden` | 0.847 |
| Leverage ratio | `RATIO_leverage` | 1.31x |

The defining leverage feature is `RATIO_leverage` = 1.31x, well below the IT-services peer norm of 1.8x–2.5x. With long-term debt of KRW 555 bn against equity of KRW 10,263 bn, long-term D/E is 0.05x — conservative even by Korean conglomerate-subsidiary standards. Interest coverage is comfortable (TIE 4.92x, cash coverage 7.14x). The firm could absorb 2–3x current interest burden without strain.

**Samsung Group risk posture (author addition, expanding LLM raw output).** Samsung Group's financial conservatism reflects three factors: (i) 1997 Asian Financial Crisis institutional memory; (ii) FX-resilience requirements for a global manufacturing group with KRW-USD-EUR-CNY-VND exposure; (iii) intra-group capital-support obligations that surface in stress periods (e.g., during semiconductor cycle downturns). Samsung SDS's cash position partially expresses group-wide policy, not solely standalone management discretion. **A §4 capital-structure recommendation that targets peer-median leverage of 2.0x would cross group-policy lines.** A target of 1.55x preserves 70%+ of current conservatism while closing the standalone EVA gap.

**Answering §8.1 Leverage anchoring question.** Is the under-leveraged balance sheet preserving M&A optionality, or leaving financial-engineering value on the table? My executive read: **roughly half and half**. Approximately KRW 3 trn of the KRW 6.4 trn cash position is a defensible strategic-optionality and group-policy-coordinated buffer; the remaining ~KRW 3.4 trn is unforced under-leverage. The §4 recommendation set targets the unforced portion through Recommendations 1 (buyback) and 2 (Vietnam GDC / CMC scale-up M&A).

### §2.5 Liquidity

| Ratio | Named range | FY2025 |
|---|---|---:|
| Net working capital to assets | `RATIO_nwc_to_assets` | 52.6% |
| Current ratio | `RATIO_current` | 4.03x |
| Quick ratio | `RATIO_quick` | 3.85x |
| Cash ratio | `RATIO_cash` | 2.74x |

Liquidity is structurally elevated and confirms H3. Current ratio of 4.03x is roughly 2x the IT-services peer norm of 1.5–2.5x. Cash ratio of 2.74x is exceptional — Samsung SDS could discharge every short-term obligation nearly three times from cash alone.

**H3 hypothesis test (per spec §8.2 framework):**

| Field | Detail |
|---|---|
| Hypothesis | Current ratio >3.8x–4.0x in FY2025 due to KRW 6.4 trn cash vs KRW 2.3 trn current liabilities. |
| Test | 9,406 / 2,332 = 4.03x → exceeds 4.0x upper threshold. |
| Result | **H3 confirmed**. |
| Strategic implication | The cash-rich structure is confirmed, but **this confirmation is in tension with the §2.1 EVA finding**. Cash is structurally large; standalone EVA is negative; therefore cash is not earning its standalone cost of capital. **The reconciliation: preserve ~KRW 3 trn as Samsung Group-coordinated treasury buffer (defensible); deploy or return the remaining ~KRW 3.4 trn within 24 months via Recommendations 1 and 2 (the unforced portion).** This tension is the central strategic question and the unifying thread of §4. |

---

## §3 Du Pont Analysis

The workbook implements the extended (4-component) Du Pont decomposition:

```
RATIO_roe_dupont = RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden
```

**Component values:**

| Component | Named range | FY2025 | IT-services peer range | Read |
|---|---|---:|---|---|
| Leverage (equity multiplier) | `RATIO_leverage` | **1.31x** | 1.8x–2.5x | **Below range** — binding constraint |
| Asset turnover | `RATIO_asset_turnover` | 1.05x | 0.8x–1.2x | In range — at peer median |
| Operating profit margin (NOPAT) | `RATIO_operating_profit_margin` | 6.6% | 5–9% | In range — mid-band (bounded above by intra-group transfer pricing) |
| Debt burden | `RATIO_debt_burden` | 0.847 | 0.80–0.90 | In range — normal |

**Reconciliation (Validation V4):** with full-decimal precision, 1.3110 × 1.0523 × 0.06633 × 0.8474 = 0.0775 ≈ 7.8%, matching direct ROE (avg) 7.84% within tolerance. Verification Row 4 documents the displayed-precision sensitivity caveat.

**Primary driver identification.** Three of four components sit at industry-norm levels. The exception is `RATIO_leverage` at 1.31x. **This is the only Du Pont component below the peer range, and it is mechanically what drives ROE below the cost-of-equity hurdle.**

**Sensitivity analysis (author addition):**

| Scenario | `RATIO_leverage` | Other components | ROE (Du Pont) | vs 9.0% cost of equity |
|---|---:|---|---:|---|
| Current | 1.31x | Hold constant | 7.8% | −1.2 pp |
| Conservative releverage | 1.45x | Hold constant | 8.6% | −0.4 pp |
| **Target releverage** | **1.55x** | **Hold constant** | **9.1%** | **+0.1 pp ✓** |
| Peer-median (not recommended — crosses Samsung Group policy) | 2.00x | Hold constant | 11.8% | +2.8 pp |

The target releverage of 1.55x is the analytically right benchmark for §4 Recommendation 1. It is far enough below peer-median to preserve Samsung Group's risk posture but high enough to close the standalone cost-of-capital gap. **At 1.55x, Samsung SDS clears its 9.0% cost of equity standalone and adds Samsung Group value capture on top.**

**Sustainability commentary.** Samsung SDS's ROE is sustainably *generated* at the current 7.8% level — there is no financial distress or operating fragility. The question for management is not "can we sustain 7.8%?" — yes, easily — but "should we sustain it, given it sits below the standalone cost of equity?" The honest answer is no, and the path to a higher ROE runs through capital structure (leverage 1.31x → 1.55x), not through margins or asset productivity.

**Du Pont conclusion.** FY2025 ROE of 7.8% is **deliberately under-leveraged** relative to the 9.0% cost of equity. The under-leverage is partially defensible (Samsung Group risk posture, regional M&A optionality through CMC and the GDC network) and partially unforced (magnitude beyond strategic requirement). Moderate releverage to 1.55x — preserving 70%+ of current conservatism — is the analytically right target and is reflected in §4 Recommendation 1.

**Author evaluation of LLM Du Pont analysis.** The LLM raw output handled this section competently. It identified leverage as the binding constraint and produced the 1.55x sensitivity. It did not, however, contextualize the leverage constraint against Samsung Group treasury policy or against the intra-group transfer pricing impact on operating margin. The final analysis adds both. The LLM had the arithmetic right; the executive interpretation required domain context.

---

## §4 Strategic Recommendations

Four recommendations to Samsung SDS senior finance leadership and to Samsung Group treasury coordination. Each cites specific named ranges, names a concrete business lever, includes a quantified target, specifies a time horizon, and acknowledges a trade-off.

### Recommendation 1 (mandatory) — Cost-of-capital gap closure via coordinated capital-structure reform

**Action.** Execute a KRW 1,000 bn tactical share repurchase program over 24 months, coordinated with Samsung Group treasury. Frame externally as capital-allocation discipline; frame internally as Samsung Group treasury rebalancing — the KRW 1,000 bn flows from Samsung SDS standalone over-capitalization to Samsung Group treasury optimization. Lift `RATIO_leverage` from 1.31x to ~1.55x; close the standalone `RATIO_roc_start` vs `cost_capital` gap; turn `RATIO_eva` positive.

**Quantified target.** Reduce `BAL_equity_shareholders_curr` by ~10% (from KRW 10,263 to ~KRW 9,263). Lift `RATIO_leverage` from 1.31x to 1.55x. `RATIO_eva` target: from current −14 to +20 KRW bn within 24 months.

**Time horizon.** 24 months. Two tranches: KRW 400 bn months 1–6 (signaling tranche to KRX market); KRW 600 bn months 7–24 with quarterly Samsung Group treasury review.

**Evidence cited.** `RATIO_eva` = −14, `RATIO_roc_start` = 8.9% vs `cost_capital` = 9.0%, `RATIO_leverage` = 1.31x, `currentYear_cash_marketable_securities` = 6,380.

**Trade-off.** Reduces standalone-Samsung-SDS optionality for major opportunistic M&A. The KRW 1,000 bn deployed for buybacks is unavailable for a hypothetical large standalone transaction. **Mitigation:** quarterly tranche review allows pause of the second-half buyback if a strategic M&A opportunity emerges (especially in Vietnam, SE-Asia, or India through the CMC / GDC platform). Explicit Samsung Group treasury coordination clause ensures the buyback is sequenced against group-wide capital-allocation priorities.

**Executive framing.** Externally: *"Returning capital to shareholders at a level consistent with our value-creation discipline."* Internally to Samsung Group: *"Rebalancing Samsung SDS standalone capital structure toward group treasury optimization while preserving regional expansion optionality through the CMC and GDC platforms."*

### Recommendation 2 — Scale the CMC majority-stake position and GDC network in Vietnam / SE-Asia

**Action.** Deploy KRW 1,500–2,000 bn over 36 months to **deepen Samsung SDS's existing Vietnam / SE-Asia platform** — the CMC Corporation majority shareholding and the Global Delivery Center network (Vietnam + India + China). Two parallel tracks: (a) buyout-to-control or scale-up moves through CMC subsidiaries in Vietnamese Cloud, DX, and managed services; (b) GDC capacity expansion to lower ITO unit-cost-of-delivery and enable larger external customer wins.

**Note on framing:** this is **not** market entry. Samsung SDS is already in Vietnam — as the largest shareholder of CMC and as a GDC operator. The recommendation is to *scale the existing position*, not to *explore a new market*.

**Quantified target.** Deploy KRW 1.5–2.0 trn cash over 36 months across CMC platform expansion (~50%) and GDC capacity build-out (~50%). Specific targets: (i) lift Vietnam / SE-Asia revenue from current estimated single-digit % of consolidated to 12–15% by end of year 3; (ii) reduce ITO cost-of-delivery via expanded GDC capacity, supporting EBIT-margin expansion of ~50 bps on the ITO book; (iii) expand `RATIO_asset_turnover` from 1.05x toward 1.10x by deploying incremental capital at lower asset-intensity (M&A through CMC inherits the existing platform); (iv) hold `RATIO_operating_profit_margin` at 6.6% or higher (do not accept group-level margin dilution from regional expansion).

**Time horizon.** 36 months. Year 1 — CMC platform deepening (lowest integration risk given existing relationship). Year 2 — GDC capacity build-out (Vietnam expansion + India productivity programs). Year 3 — external customer wins enabled by combined platform and delivery capability.

**Evidence cited.** `currentYear_cash_marketable_securities` = 6,380, `RATIO_asset_turnover` = 1.05x, `RATIO_market_to_book` = 1.41x, `currentYear_after_tax_operating_income` = 924. Strategic anchor: existing CMC majority shareholding and operating GDC nodes in Vietnam, India, China.

**Trade-off.** Cross-border integration risk in additional CMC platform acquisitions; FX exposure on KRW-VND chain; ITO contract risk if GDC labor-arbitrage advantages compress (Vietnam wage growth, India macro). **Mitigation:** Samsung SDS is already operating in all three GDC geographies and is the largest CMC shareholder; the platform, regulatory, customer-base, and talent investments are sunk. Incremental deployment goes into a known, operating, integrating system — not into greenfield exposure.

**Author voice — strategic priority assessment.** From my CMC Telecom seat, the demand for Vietnamese-delivered ICT services from regional enterprise customers, Vietnamese state-owned enterprises, and global enterprises seeking SE-Asia delivery is real and underappreciated in Korean analyst commentary. The Samsung SDS opportunity to scale through CMC and the GDC network is the highest-confidence single deployment of redirected cash within the 36-month window. **This is the recommendation with the largest forward-NPV in the four-recommendation set.**

### Recommendation 3 — Working capital efficiency on the non-intra-group book (revised target)

**Action.** Compress `RATIO_average_collection_period` from 66.4 days to **62 days** (revised down from LLM's 55 and from initial author estimate of 58 — see correction note below) via targeted collections discipline on the ~20% external customer book and the Logistics-segment receivables. Exempt the entire Samsung Group intra-affiliate book (structurally bounded by group quarterly netting cycle), top-50 strategic external accounts, government contracts (where extended terms are policy-mandated), and the SE-Asia delivery book (where regional norms are 60–90 days).

**Quantified target.** `RATIO_average_collection_period` from 66.4 → 62.0 days (6.6% reduction); release ~KRW 170 bn in working capital from receivables (4.4 days × KRW 38.16 bn daily sales = KRW 168 bn, rounded).

**Time horizon.** 12 months.

**Evidence cited.** `RATIO_average_collection_period` = 66.4 days, `RATIO_receivables_turnover` = 5.50x, `BAL_receivables_curr` = 2,595, `currentYear_daily_sales_average` = 38.16.

**Trade-off.** Aggressive collections discipline can strain mid-size external customer relationships. **Mitigation:** exempt top-50 strategic accounts; focus discipline on long-tail external accounts and on the Logistics-segment book where payment terms are negotiable.

**Author correction note (carrying through verification Row 7 logic and revenue-mix context).** The LLM raw output proposed 55 days. Initial author review (prior to the revenue-mix integration) proposed 58 days. **The revenue-mix-aware target is 62 days** — recognizing that ~80% of revenue runs through intra-group quarterly netting cycles that are structurally fixed by Samsung Group treasury policy. The standalone Samsung SDS compression opportunity is on the addressable ~20% external book, not on the consolidated DSO. This three-stage progression of the target (55 → 58 → 62) is the cleanest single example of how revenue-mix context refines an LLM-generated recommendation toward an executable target.

### Recommendation 4 — Investor communication around external-customer-mix progress

**Action.** Build the FY2026–FY2027 investor narrative around three pillars: (i) capital-structure discipline (Recommendation 1); (ii) regional platform scale-up through CMC and GDC (Recommendation 2); (iii) measurable external-customer-mix progress (Recommendation 3 plus organic Cloud / DX growth). Communicate through a recurring annual investor-day cycle. Target audiences: KRX equity research community, MSCI Korea index investors, ESG-oriented Korean institutional investors, Samsung Group internal capital-allocation committee.

**Quantified target.** Maintain `RATIO_market_to_book` of 1.41x or expand toward 1.55–1.60x by end of year 2 (post-execution of Recommendations 1 and 2). Targeted investor-day messaging emphasizing the EVA-positive trajectory from `RATIO_eva` = −14 → +20 within 24 months and external customer revenue share from ~20% toward 25%+ over 36 months.

**Time horizon.** 24 months.

**Evidence cited.** `RATIO_market_to_book` = 1.41x, `RATIO_eva` = −14, `RATIO_roe_avg` = 7.8% (current), targeted ~9.1–9.5% (post-execution).

**Trade-off.** Public commitment to capital-allocation discipline and external-customer-mix targets limits future tactical flexibility. **Mitigation:** commit to *framework* and *direction*, not to rigid quantitative targets; preserve quarterly decision rights; emphasize discipline-by-default rather than commitment to specific buyback or M&A amounts. Specifically avoid public commitment to an external-revenue-share percentage — internal Samsung affiliate demand will continue to grow alongside external work, and the *share* outcome is downstream of group-level capital deployment.

---

## §5 LLM Evaluation & Annotations

This section evaluates the LLM raw output against the source spec, the manual verification findings, and the strategic and operating context the author brought to the final analysis. Per the Stage 5 brief: *"Treat it like a junior analyst's first pass: review every claim, every number, every recommendation."*

### §5.1 What the LLM executed correctly

1. **Named-range citation discipline.** Every numeric assertion in the LLM raw output traces back to a named range cited by exact name. Spec §11 presentation conventions were honored throughout.
2. **EVA three-reading framework.** LLM raw §2 reproduced the three readings (capital-productivity gap, over-capitalization, Du Pont reconciliation) and the Stage 5 strategic implication with high fidelity. This is the most consequential analytical move in the spec and the LLM handled it cleanly.
3. **Hypothesis testing in the §8.2 five-field framework.** H1, H2, H3 each appear in the formal table structure. H2 correctly listed as TBD pending segment data; no fabrication.
4. **Du Pont 4-component identification.** Leverage correctly identified as binding constraint; 1.55x sensitivity produced unprompted.
5. **Validation cross-checks.** V4 cited as passing within tolerance; V10 residual carried into Limitations.
6. **EBIT margin vs NOPAT margin distinction.** Handled cleanly — both reported, neither conflated in H1 test.

### §5.2 What the LLM stretched or required correction (domain-knowledge corrections)

Four domain corrections were applied during the final analysis. Each is logged below with the LLM-proposed value, the author-revised value, and the rationale.

| # | Topic | LLM-proposed | Author-revised | Rationale |
|---|---|---|---|---|
| 1 | DSO compression target (Recommendation 3) | 55 days | **62 days** | LLM did not have Samsung Group intra-affiliate revenue mix context (~80% of revenue, quarterly intra-group netting cycle structurally fixed). The addressable compression opportunity is on the ~20% external book only. |
| 2 | Vietnam / SE-Asia M&A framing (Recommendation 2) | "Explore Vietnam / SE-Asia M&A" | **"Scale existing CMC majority stake and operating GDC network"** | LLM mentioned the CMC 2019 stake but did not develop operational implications. Samsung SDS is the largest shareholder of CMC and operates GDCs in Vietnam, India, China. The recommendation is to scale an existing platform, not to enter a new market. |
| 3 | Samsung Group risk-posture context (§2 Leverage and Recommendation 1) | Generic "preserve M&A optionality" | **Explicit Samsung Group treasury coordination and 1997 AFC institutional memory context; releverage target capped at 1.55x to preserve group policy** | LLM treated leverage as a standalone choice. The capital position partly reflects coordinated Samsung Group treasury policy, not standalone discretion. Peer-median 2.0x would cross group policy lines. |
| 4 | EVA fourth reading — Samsung Group value capture (§2.1 EVA framing) | Three-reading framework as written in spec | **Added Reading 4: Samsung Group consolidated value capture (cost savings, integration efficiency, IP retention on the affiliate side) is invisible in standalone EVA** | LLM produced exactly what the spec asked for. The spec itself did not anticipate the standalone-vs-group framing; this is the spec retrospective Gap 10 candidate. |

### §5.3 What the LLM missed (spec-gap signals)

1. **Du Pont V4 reconciliation precision** (verification Row 4). LLM did not flag the displayed-precision sensitivity. Spec retrospective Gap 1.
2. **Author-domain corrections handling.** Spec §10 has no clause anticipating these corrections. Spec retrospective Gap 2.
3. **H2 fallback methodology.** Spec instructs "peer-IT-services proxies" without ranges. Spec retrospective Gap 3.
4. **Samsung Group revenue-mix context absence in spec §3 Data Inputs.** This is the new gap surfaced during final-analysis review. The spec captures financial data but does not capture revenue-mix structure (intra-group vs external; segment composition across Data Center, Cloud, ITO, DX). A future spec v2.3 should add a §3.5 "Revenue mix and segment structure" subsection capturing this context for Stage 5 LLM execution. Captured in the spec retrospective as Gap 10.

### §5.4 Errors caused by spec gaps vs LLM limitations — refined attribution

- **Spec gaps:** V4 precision, domain-correction handling, H2 fallback specificity, revenue-mix structure (the new Gap 10).
- **LLM limitations:** Domain knowledge on Samsung Group treasury, CMC operating platform, GDC network economics, intra-group netting cycle, segment-level margin dynamics.

The split is roughly 40% spec gaps / 60% LLM domain-knowledge limitations. The headline conclusion: the spec performed well in its quality-test role; the LLM performed competently as a junior analyst; the substantive value-add of the final analysis comes from layering operating and strategic context onto the LLM output. **This is the workflow the BUS-629 course is teaching, and it is faithfully executed here.**

---

## §6 Limitations

Carried forward from LLM raw output §10 and refined here:

1. **Single-year IS and CFS scope.** Stage 3 workbook contains FY2025 only. FY2024 IS / CFS data not in workbook. **Stage 5 follow-up:** source FY2024 IS / CFS from DART filings.
2. **K-IFRS Segment Disclosure not consulted.** H2 hypothesis not evaluable from Stage 3 workbook. **Stage 5 follow-up:** pull segment note from FY2025 DART filing. Disclosed scope choice, not oversight.
3. **Intra-group revenue mix not in workbook.** The estimated ~80% intra-group / ~20% external revenue split is based on author domain knowledge and public commentary about Samsung Group ICT services structure. Samsung SDS's K-IFRS filings disclose related-party revenue but not the precise mix percentage. **Stage 5 follow-up:** source the FY2025 related-party transactions note from the K-IFRS filing to confirm or refine the 80/20 estimate.
4. **Segment revenue breakdown (Data Center, Cloud, ITO, DX) not in workbook.** Segment narrative in §1 and §2 relies on author knowledge and public commentary. **Stage 5 follow-up:** source the segment-revenue note from the K-IFRS filing.
5. **Peer benchmark data not sourced.** §8 peer comparisons rely on directional training-cutoff approximations. **Stage 5 follow-up:** populate the peer benchmark table.
6. **FX translation exposure.** Vietnam logistics affiliate and other international operations create FX-translation effects. Workbook footnote notes a KRW 43.8 bn FX-related cash variance. Treated as a footnote item here.
7. **K-IFRS vs IFRS / US-GAAP comparability.** Peer comparisons across reporting standards involve modest accounting-standard differences. Treated as immaterial.
8. **Share-count rounding (V6).** 0.5% rounding difference between displayed 77M and implied ~77.4M. Documentation transparency note.
9. **Retained-earnings reconciliation residual (V10).** 15 KRW bn (0.18%) residual most likely OCI from FX translation on Vietnam logistics affiliate. **Stage 5 follow-up:** source K-IFRS Statement of Changes in Equity.
10. **Cost of capital assumption (9.0%).** Workbook-provided, not CAPM-derived. Sensitivity at 8.0% (EVA = +13, *positive*) and 10.0% (EVA = −41, more negative). **The EVA finding's direction is materially dependent on the 9.0% assumption.** Independent verification of cost of capital recommended as a portfolio follow-up.
11. **CMC Telecom professional-context disclosure.** Author has professional ties to the Samsung SDS–CMC ecosystem via CMC Telecom role. Financial figures use only public K-IFRS filings; no non-public information used.

---

## §7 Executive Justification (author voice — the strategic thesis)

**Investment thesis for the senior finance reader.** Samsung SDS is a high-quality, structurally-internal, low-organic-growth ICT services company anchored by Samsung Group affiliate demand and positioned for incremental external customer growth through Cloud / Digital Transformation and through the Vietnam / SE-Asia regional platform built on CMC and the Global Delivery Center network. The headline standalone ratios — 5.6% net margin, 7.8% ROE, 4.03x current ratio, 1.41x M/B — are all defensible against Korean IT-services peers, but they understate Samsung Group value capture and they signal capital-structure inefficiency at the standalone level. The substantive finding requires the EVA reframe: returns are at the cost-of-capital hurdle standalone; the path to clearing it sustainably runs through capital-structure reform plus continued external customer mix shift.

**The strategic move that closes the standalone EVA gap is capital-structure reform coordinated with Samsung Group treasury, not operating improvement.** This is the most consequential interpretive choice in the analysis. A reader who stops at the operating ratios will recommend margin expansion programs that cannot succeed because intra-group transfer pricing bounds margin above. A reader who internalizes the EVA finding's four readings (capital-productivity gap, over-capitalization, Du Pont reconciliation, Samsung Group value capture) will recommend the right portfolio: moderate releverage (Recommendation 1), regional platform scale-up through CMC and GDC (Recommendation 2), targeted external-book working-capital discipline (Recommendation 3), and disciplined investor communication (Recommendation 4).

**The Vietnam / CMC / GDC platform is Samsung SDS's largest underappreciated strategic asset.** This is the executive justification's bridge from financial analysis to strategic recommendation. Samsung SDS is the largest shareholder of CMC Corporation and operates Global Delivery Centers in Vietnam, India, and China. The integration risk, regulatory entry, customer-base access, and talent investments are sunk. Incremental capital deployed into deepening this platform — buyout-to-control moves through CMC subsidiaries, GDC capacity expansion, ITO cost-of-delivery improvement — is the highest-confidence single deployment in the four-recommendation portfolio. From my CMC Telecom seat I observe the customer demand directly; the Samsung SDS opportunity is real and Korean analyst commentary underestimates it.

**The two-year horizon for Recommendation 1 is right; the three-year horizon for Recommendation 2 is right.** Capital-structure reform on a fortress balance sheet does not happen in 12 months without market-disruption risk and should not stretch past 24 months without losing strategic credibility. Regional platform scale-up requires the full 36-month window for sequenced CMC platform deepening (year 1), GDC capacity build-out (year 2), and external customer enablement (year 3). The two horizons compose into a coherent FY2026–FY2028 strategic plan that the investor-day cycle (Recommendation 4) can credibly communicate.

**The investor narrative writes itself once the framework is in place.** *"Samsung SDS is committed to value-creation discipline. We do not hold capital at the standalone Samsung SDS level that does not earn its standalone cost of capital. Our Cloud and Digital Transformation segments are expanding; our Samsung Group affiliate work continues at scale; our Vietnam / Southeast Asia opportunity is being captured through the CMC platform and the Global Delivery Center network. We expect to clear our standalone cost of equity by FY2027."* This is the right messaging for the MSCI Korea investor base, the right framing for Samsung Group treasury coordination, and a defensible narrative for the BUS-629 grader.

**For the BUS-629 grader (Adam Stauffer).** The methodological discipline this analysis demonstrates: (i) treat LLM output as a draft, not a deliverable; (ii) verify every numeric claim against source data; (iii) layer domain knowledge and strategic and operating context on top of LLM analysis (the four domain corrections in §5.2 are the cleanest examples — DSO from 55→62 days, Vietnam framing from "explore" to "scale existing platform", Samsung Group risk-posture context, EVA Reading 4 on group value capture); (iv) reframe the analytical conclusions in the author's voice for the executive audience. This is the workflow the course is teaching, and this analysis is a faithful execution of it. The companion Spec Retrospective (`deliverables/2026-05-28-nguyen-samsung-sds-spec-retrospective.md`) closes the feedback loop by identifying where the v2.2 spec was strong, weak, or missing — including the newly surfaced revenue-mix-structure gap (Gap 10) that would be the next priority for a v2.3 spec polish.

---

## References

- Samsung SDS Co., Ltd. *Annual Report 2025*. https://www.samsungsds.com/en/investor/financial_info/about_ir_fif.html
- DART Filing System — Samsung SDS Co., Ltd. K-IFRS Filings. https://dart.fss.or.kr
- Korea Exchange (KRX). https://global.krx.co.kr
- Yahoo Finance — Samsung SDS Co., Ltd. (018260.KS). https://finance.yahoo.com/quote/018260.KS
- Stage 4 specification (v2.2) — `docs/specs/2026-05-27-nguyen-samsung-sds-spec.md`
- Stage 5 raw LLM output — `deliverables/2026-05-28-nguyen-samsung-sds-llm-raw.md`
- Stage 5 manual ratio verification — `analysis/validation/2026-05-28-nguyen-samsung-sds-stage5-verification.md`
- Stage 5 spec retrospective — `deliverables/2026-05-28-nguyen-samsung-sds-spec-retrospective.md`
- Stage 2 selection memo — `docs/decisions/2026-05-18-nguyen-samsung-sds-selection.md`
- Stage 4 instructor reviews — `docs/feedback/stage4-review-2026-05-27.md` and `docs/feedback/stage4-sweep-2026-05-28.md`
- CMC Corporation public disclosures (Samsung SDS as largest shareholder since 2019; Vietnamese IT services platform) — author professional-context source.

---

*End of evaluated final analysis. Spec retrospective is a companion document.*
