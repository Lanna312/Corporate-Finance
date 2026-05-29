---
template: stage5-verification
purpose: "Manual ratio verification — recompute seven ratios by hand from Stage 3 financial data and compare to the LLM's stated values from the raw output. Flag and explain any discrepancies. Where ratio interpretation depends on revenue-mix or segment structure, document the context."
author: Nguyen Lan Anh
date: 2026-05-28
company: Samsung SDS Co., Ltd. (KRX: 018260)
courses: [BUS-629]
stage: 5
source_workbook: models/builds/2026-05-21-nguyen-samsung-sds-financials.xlsx
llm_raw_output: deliverables/2026-05-28-nguyen-samsung-sds-llm-raw.md
spec: docs/specs/2026-05-27-nguyen-samsung-sds-spec.md (v2.2)
---

# Stage 5 Manual Ratio Verification — Samsung SDS FY2025

This file fulfills Stage 5 Deliverable #2 (Manual ratio verification artifact — 10% of Stage 5 score). Seven ratios are recomputed by hand from the Stage 3 financial data and compared to the LLM's stated values in `2026-05-28-nguyen-samsung-sds-llm-raw.md`.

**Selection logic.** Ratios picked across all six categories of the spec, with intentional bias toward those a Stage 5 LLM is most likely to get wrong: anything involving averaging conventions, start-of-year denominators, day-count conventions (365 vs 360), or multi-component reconciliation. Per the Stage 5 brief: *"Discrepancies are not failures — they are the most informative rows in the table."*

**Three sources of ratio values are referenced.** Per the brief's framework:

| Source | Where it comes from | Used here as |
|---|---|---|
| Template's auto-computed | Stage 3 workbook Ratios tab (Excel formulas) | Sanity reference only — not the column being graded |
| LLM's stated | Stage 5 raw LLM output | The "LLM's value" column |
| My manual | Recomputed by hand from Stage 3 data | The "Manual value" column |

The verification compares **Manual vs LLM**. Where the template's auto-computed value differs from both, that is itself a finding (typically a workbook decimal-precision artifact).

**Strategic and operating context for ratio interpretation.** Several rows below reference the intra-group revenue structure (approximately 80% of Samsung SDS revenue is generated from Samsung Group affiliate work; ~20% from external customers) and the resulting structural impact on ratios — particularly DSO, where Samsung Group quarterly intra-affiliate netting cycles structurally elevate the consolidated DSO. The verification arithmetic is independent of this context; the *interpretation* of the result is not. Notes that incorporate this context are flagged.

---

## Verification table

| # | Ratio | Category | Formula (named-range notation) | Manual value (arithmetic shown) | Template (workbook) value | LLM's value | Match? | One-line note |
|---|---|---|---|---|---:|---:|:---:|---|
| 1 | Return on Capital (start) | Profitability | `currentYear_after_tax_operating_income` / `startYear_total_capitalization` | 924 / 10,422 = 0.08867 = **8.87%** | 8.9% | 8.9% | ✓ | Match within rounding. LLM correctly used start-of-year capitalization denominator per spec V3; did not erroneously use average or end-of-year. Match confirms the spec's "start" convention was honored. **Interpretive note:** 8.87% sits 13 bps below `cost_capital` (9.0%) — the standalone-firm capital-productivity finding. Standalone EVA is correspondingly negative; Samsung Group value capture sits outside this calculation (see final analysis §2.1 Reading 4). |
| 2 | Average Collection Period (DSO) | Efficiency | `startYear_receivables` / `currentYear_daily_sales_average`, with `currentYear_daily_sales_average` = `INC_sales` / **365** | 2,534 / (13,930 / 365) = 2,534 / 38.164 = **66.4 days** | 66.4 days | 66.4 days | ✓ | Match. LLM correctly used **365-day** convention per spec (not 360-day) and start-of-year receivables (not end-of-year). Either error would have produced a noticeably different value: 360-day would give 65.5 days; using end-of-year receivables (2,595) would give 68.0 days. Spec specificity prevented both common errors. **Interpretive note — revenue mix:** ~80% of Samsung SDS revenue flows through quarterly intra-Samsung-Group affiliate netting cycles, structurally elevating consolidated DSO. The standalone Samsung SDS DSO compression opportunity is on the ~20% external book only; the intra-group portion is structurally fixed by Samsung Group treasury policy. This context revises the LLM-proposed 55-day compression target to 62 days (final analysis Recommendation 3). |
| 3 | Economic Value Added (EVA) | Performance | `currentYear_after_tax_operating_income` − (`cost_capital` × `startYear_total_capitalization`) | 924 − (0.090 × 10,422) = 924 − 937.98 = **−13.98 ≈ −14 KRW bn** | (14) | (14) | ✓ | Match. The critical check is that LLM used `startYear_total_capitalization` (10,422), not `currentYear_total_capitalization` (10,818). Had LLM used current-year capitalization, EVA would have been 924 − (0.09 × 10,818) = −49.6 KRW bn — over 3x the magnitude. Spec's explicit "startYear" denominator prevented this. **Flagged finding confirmed.** **Interpretive note — Samsung Group value capture:** standalone EVA at −14 understates Samsung Group-level value creation. Intra-group cost savings, integration efficiency, and IP retention on the affiliate side accrue to Samsung Group consolidated economics but do not appear in the Samsung SDS standalone P&L. This is the fourth reading added in the final analysis §2.1. |
| 4 | ROE (Du Pont 4-component, extended) | Du Pont | `RATIO_leverage` × `RATIO_asset_turnover` × `RATIO_operating_profit_margin` × `RATIO_debt_burden` | Using full-decimal precision: (13,454/10,263) × (13,930/13,238) × (924/13,930) × (783/924) = 1.3110 × 1.0523 × 0.06633 × 0.8474 = **0.0775 ≈ 7.75%** | 7.8% | 7.8% | ✓ | Match within tolerance. **Note on reconciliation precision:** if Du Pont is computed using *displayed* (2-decimal) component values rather than full-decimal — i.e., 1.31 × 1.05 × 0.066 × 0.847 — the product is 0.0769 ≈ 7.7%, missing direct ROE (7.8%) by 0.1pp. Validation Rule V4 tolerance is ±0.001 (0.1%), so this is at the boundary. **Stage 5 implication:** the V4 tolerance must be applied against *unrounded* component arithmetic, or relaxed slightly. LLM raw output cited V4 as passing within tolerance — concurred with conclusion but the working should disclose the rounding-sensitivity caveat. Captured in spec retrospective Gap 1. |
| 5 | Quick Ratio | Liquidity | (`currentYear_cash_marketable_securities` + `BAL_receivables_curr`) / `currentYear_liabilities_current` | (6,380 + 2,595) / 2,332 = 8,975 / 2,332 = **3.848x ≈ 3.85x** | 3.85x | 3.85x | ✓ | Match. The LLM correctly used the spec's formula composition — adding receivables to cash. A common error would be using only cash (giving 2.74x = Cash Ratio, a different ratio). Another error would be subtracting inventory from current assets (an alternative Quick Ratio formula); that gives (9,406 − 15) / 2,332 = 4.027x ≈ 4.03x, which would *equal* the Current Ratio because inventory is negligible. Spec's explicit formula composition prevented both. |
| 6 | Times Interest Earned | Leverage | `INC_ebit` / `INC_interest_expense` | 957 / 194 = **4.933x ≈ 4.92x** | 4.92x | 4.92x | ✓ | Match within rounding. Workbook displays 4.92x; manual gives 4.93x. The 0.01x difference is a workbook display-precision artifact. No analytical concern. **Interpretive note:** TIE of 4.92x against a long-term debt position of just KRW 555 bn signals that interest expense is largely operational (lease-related or trade-financing related, not financial-debt-related). The leverage component of the Du Pont decomposition is bounded by capital structure, not by interest coverage. |
| 7 | Inventory Turnover | Efficiency | `INC_cost_goods_sold` / `startYear_inventory` | 11,510 / 19 = **605.79x** | 605.77x | 605.77x | ✓ | Match within rounding (605.79 vs 605.77 = 0.003% difference, workbook internal-precision artifact). **Important interpretive caveat:** the extreme value (605x) is a symptom of services-business reality — inventory is materially zero (KRW 19 bn against KRW 11,510 bn COGS). The ratio is mathematically correct but analytically uninformative. The associated `RATIO_days_inventory` of 0.6 days (manual: 19 / (11,510/365) = 19 / 31.534 = 0.603 ≈ 0.6 days) makes the point cleaner. **Stage 5 implication:** report both, but emphasize Days-in-Inventory in narrative; do not treat 605x as a competitive-advantage signal. |

---

## Summary statistics

| Metric | Result |
|---|---:|
| Total ratios verified | 7 |
| Categories covered | 6 (Profitability, Efficiency, Performance, Du Pont, Liquidity, Leverage) |
| Exact matches (Manual = LLM, to display precision) | 7 |
| Discrepancies (Manual ≠ LLM) | 0 |
| Material flags / caveats | 5 (Du Pont rounding sensitivity; Inventory Turnover analytical caveat; intra-group DSO structure; Samsung Group EVA value-capture context; V6 / V10 carryover) |

**Headline:** All seven LLM-stated values match manual recomputations within rounding tolerance. The match itself is a meaningful finding — it demonstrates that **the spec's named-range specificity successfully constrained LLM output to the workbook's exact conventions**, preventing the common Stage 5 LLM errors the verification table is designed to catch (averaging vs start-of-year, 360 vs 365 day-count, formula composition variants).

The substantive verification value beyond the match itself comes from the **interpretive notes** — particularly the intra-group revenue-mix context for DSO (Row 2) and the Samsung Group value-capture context for EVA (Row 3). These contexts are not in the spec and were not visible to the cold-context LLM; they are documented here as the bridge to the final analysis interpretation.

---

## Substantive observations from the verification process

### Observation 1 — Spec specificity prevented predictable arithmetic errors

Five of the seven ratios checked are exactly the type the Stage 5 brief flags as "most likely to get wrong":
- ROC start-of-year vs average denominator (Row 1)
- DSO day-count and receivables-balance convention (Row 2)
- EVA start-of-year vs current-year capitalization (Row 3)
- Du Pont 4-component vs 3-component reconciliation (Row 4)
- Quick Ratio formula composition variants (Row 5)

In every case, the spec's explicit named-range formulas — `startYear_total_capitalization`, `currentYear_daily_sales_average` (with /365 in the named range definition), `RATIO_debt_burden` as the fourth Du Pont term, etc. — constrained the LLM to a single correct interpretation. The match results are not a failure of the verification table to find issues; they are a success of the spec's design.

### Observation 2 — Du Pont reconciliation precision (Row 4) is a real spec gap

The Du Pont reconciliation passes when computed against full-precision component values (7.75% ≈ 7.8% direct). It passes only marginally when computed against displayed 2-decimal components (7.69% vs 7.8% direct = 0.1pp gap, at V4 tolerance boundary). **The spec should specify that V4 reconciliation is to be evaluated against unrounded arithmetic**, or alternatively relax V4 to ±0.5% to accommodate display precision. This is a spec-improvement item for a future v2.3 — captured in the Stage 5 spec retrospective at `deliverables/2026-05-28-nguyen-samsung-sds-spec-retrospective.md` as Gap 1.

### Observation 3 — DSO interpretation depends on revenue-mix context not in the spec

The arithmetic of `RATIO_average_collection_period` = 66.4 days is unambiguous and the LLM computed it correctly. The *interpretation* — specifically, what compression target is achievable — depends on context the spec did not capture: approximately 80% of Samsung SDS revenue flows through Samsung Group affiliate work subject to quarterly intra-group netting cycles set at Samsung Group treasury policy. The addressable compression opportunity is on the ~20% external customer book only. A cold-context LLM lacking this context produced a 55-day target; revenue-mix-aware interpretation produces a 62-day target. **The spec should capture revenue-mix structure to enable correct interpretation** — captured in the Stage 5 spec retrospective as new Gap 10.

### Observation 4 — Samsung Group value capture is invisible in standalone EVA (Row 3)

The standalone EVA arithmetic is correct: −14 KRW bn. But the interpretation requires recognizing that Samsung SDS captures significant value on the Samsung Group affiliate side (cost savings, integration efficiency, IP retention) that does not appear in its standalone P&L. The final analysis adds this as Reading 4 in §2.1. **The spec should anticipate the standalone-vs-group framing for any group-affiliate-anchored company** — captured in spec retrospective Gap 10.

### Observation 5 — Inventory Turnover (Row 7) is a category-anomaly signal

The extreme value (605x) is a real-data artifact of a services business with negligible physical inventory, not an analytical issue with the formula. The Stage 5 final analysis avoids framing this as a competitive-advantage signal and emphasizes Days-in-Inventory (0.6 days) in narrative.

### Observation 6 — Validation Rule V10 carryover (15 KRW bn residual)

Per the spec v2.2 §7 Note on V10, the retained-earnings roll-forward shows a 15 KRW bn residual (0.18%) attributable to other comprehensive income, equity-method gains/losses, or treasury stock. Confirmed in Stage 4 v2.2 work; well within the ±50 KRW bn tolerance. The substantive driver (Vietnam logistics affiliate FX translation, most likely) is documented in the Stage 5 final analysis Limitations section.

---

## Verification methodology note

All manual computations used the Stage 3 workbook values as the source-of-truth inputs. Arithmetic was performed using full decimal precision (not workbook display precision). Display rounding was applied only at the final reported value, matching the spec's `0.0%`, `0.00x`, and `66.4 days` formatting conventions.

For ratios where the workbook's auto-computed value differed from a from-scratch recomputation by more than 0.5% (none in this batch — all within rounding artifact), the workbook formula would have been cross-checked against the Stage 3 workbook's Excel formula-bar text. No such investigation was required for the seven ratios verified here.

The interpretive notes draw on author professional context (Samsung SDS revenue mix structure; Samsung Group treasury policy; CMC platform and Global Delivery Center network strategy). The arithmetic itself is independent of this context; the interpretation is not.

---

## Cross-references

- **LLM raw output:** `deliverables/2026-05-28-nguyen-samsung-sds-llm-raw.md` (the input to this verification)
- **Final analysis:** `deliverables/2026-05-28-nguyen-samsung-sds-final-analysis.md` (where these verifications are integrated with author corrections, strategic and operating context, and executive voice)
- **Spec retrospective:** `deliverables/2026-05-28-nguyen-samsung-sds-spec-retrospective.md` (where Observation 2 — Du Pont reconciliation precision — is logged as Gap 1, Observation 3 — DSO revenue-mix context — and Observation 4 — Samsung Group value capture context — are logged as Gap 10)
- **Spec v2.2:** `docs/specs/2026-05-27-nguyen-samsung-sds-spec.md` (the spec whose specificity is being tested)
