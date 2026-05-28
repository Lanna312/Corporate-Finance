---
template: hil-iteration
purpose: "Annotated diff documenting the Stage 4 spec iteration from v1.0 → v2.1, gap-by-gap"
author: Nguyen Lan Anh
date: 2026-05-27
company: Samsung SDS Co., Ltd.
ticker: 018260.KS
courses: [BUS-629]
stage: 4
spec_file: docs/specs/2026-05-27-nguyen-samsung-sds-spec.md
companion: deliverables/prompt-log.md
---

# Stage 4 HIL Iteration — Samsung SDS Spec, v1.0 → v2.1 Annotated Diff

This document is the Stage 4 Human-in-the-Loop evidence file (rubric criterion 4 — "Spec craft + prompt log quality"). It accompanies the prompt log and the spec by showing, gap-by-gap, where the v1.0 LLM draft was wrong, why my spec caused the gap, and what changed in v2.x.

Three substantive revisions are documented below. Each entry follows: **Before** (v1.0 excerpt) → **After** (v2.1 excerpt) → **Gap explanation** → **Why this matters for Stage 5**.

---

## Iteration 1 — Named Range Conventions: year-suffix vs `_curr`/`_prior`

### Before — v1.0 §3 Data Inputs (excerpt)

```
| Named Range                          | FY2024 | FY2025 |
|--------------------------------------|-------:|-------:|
| BAL_assets_total_2024                | 13,238 |        |
| BAL_assets_total_2025                |        | 13,454 |
| INC_sales_2025                       |        | 13,930 |
| BAL_equity_total_2025                |        | 10,263 |
```

### After — v2.1 §4 Named Range Conventions (excerpt)

```
| Named range                          | FY2024 (prior) | FY2025 (curr) |
|--------------------------------------|---------------:|--------------:|
| BAL_assets_total_*                   |         13,238 |        13,454 |
| BAL_equity_shareholders_*            |          9,705 |        10,263 |
| INC_sales                            |              — |        13,930 |

> Replace `*` with `curr` for FY2025 or `prior` for FY2024.
```

### Gap explanation

The Stage 3 workbook uses `_curr` / `_prior` suffixes for balance-sheet items (year-agnostic, reusable) and no suffix for income-statement items (since IS is single-year only in the workbook). My v1.0 spec invented a year-suffix convention (`_2024`, `_2025`) that does not exist anywhere in the workbook. A Stage 5 LLM fed only the spec would generate formulas referencing names that don't resolve — or worse, look correct in isolation but mismatch the actual workbook structure.

### Why this matters for Stage 5

The whole point of the spec is to let an LLM with no prior context reproduce the analysis. If named ranges in the spec don't match the workbook, the spec breaks its own quality test. Rubric criterion 1 ("Every input value present numerically; architecture fully defined") is unearnable without this fix.

---

## Iteration 2 — Du Pont decomposition: 3-component → 4-component extended

### Before — v1.0 §5.6 Du Pont Decomposition

```
**5.6 Du Pont Decomposition (3-step)**

| Component                  | Named Range                  | Formula                                     |
|----------------------------|------------------------------|---------------------------------------------|
| Net Margin                 | RATIO_dupont_net_margin_2025 | INC_net_income_2025 / INC_sales_2025        |
| Asset Turnover             | RATIO_dupont_at_2025         | INC_sales_2025 / BAL_assets_total_avg_2025  |
| Equity Multiplier          | RATIO_dupont_em_2025         | BAL_assets_total_avg / BAL_equity_total_avg |
| ROE Du Pont                | RATIO_roe_dupont_2025        | Margin × Turnover × Equity Multiplier       |
```

### After — v2.1 §6.6 Du Pont System (4-component extended)

```
| Component                       | Named range                     | Formula                                                                                              | FY2025 |
|---------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------|-------:|
| ROA (Du Pont)                   | RATIO_roa_dupont                | RATIO_asset_turnover × RATIO_operating_profit_margin                                                  |   7.0% |
| ROE (Du Pont, extended)         | RATIO_roe_dupont                | RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden             |   7.8% |
```

### Gap explanation

The Stage 3 workbook implements the **extended** (4-component) Du Pont:
- `RATIO_leverage` = `currentYear_assets_total` / `currentYear_equity` = 1.31x
- `RATIO_asset_turnover` = `INC_sales` / `startYear_total_assets` = 1.05x
- `RATIO_operating_profit_margin` = NOPAT / `INC_sales` = 6.6%
- `RATIO_debt_burden` = `INC_net` / NOPAT = 0.847

Product: 1.31 × 1.05 × 0.066 × 0.847 = **7.78%** ≈ workbook ROE (avg) of 7.8% ✓

The classic 3-component Du Pont (Margin × Turnover × Equity Multiplier) would have given 5.6% × 1.05 × 1.31 = 7.7%, close numerically but using `RATIO_profit_margin` (net) instead of `RATIO_operating_profit_margin` (NOPAT) × `RATIO_debt_burden`. The 4-component form decomposes the after-interest impact via `RATIO_debt_burden` — a richer analytical decomposition that the workbook author chose deliberately.

### Why this matters for Stage 5

Stage 5 §7 (Du Pont Decomposition) must reconcile component-by-component back to direct ROE. A 3-component spec would force the executor to either ignore `RATIO_debt_burden` (failing reconciliation) or re-derive a different formula (defeating the purpose of having a spec). Rubric criterion 2 ("All 25+ ratios with correct formulas in named-range notation") and Validation Rule V4 (Du Pont reconciliation) both depend on this fix.

---

## Iteration 3 — Negative EVA finding: from oversight to mandatory analysis requirement

### Before — v1.0 §5.1 Performance (excerpt)

```
| Ratio                   | Named Range          | Formula                                                                                |
|-------------------------|----------------------|-----------------------------------------------------------------------------------------|
| Economic Value Added    | RATIO_eva_2025       | INC_nopat_2025 − (BAL_capital_invested_avg_2025 × WACC_2025)                            |
```

(No flag, no value, no analytical guidance. Just a formula.)

### After — v2.1 §6.1 Performance (excerpt) + cross-references in §8 and §10

```
| Ratio                   | Named range                     | Formula                                                                                                   | FY2025  |
|-------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------|--------:|
| Economic value added    | RATIO_eva                       | currentYear_after_tax_operating_income − (cost_capital × startYear_total_capitalization)                  | **(14)** |

> Flagged finding: EVA is slightly negative (−14 KRW bn) despite positive ROC of 8.9%, because the start-of-year invested capital of 10,422 multiplied by the 9.0% cost of capital (938) exceeds the after-tax operating income of 924. Stage 5 must address this in §8 and §10.
```

Plus in v2.1 §8 *Analysis Requirements*:

```
6. Mandatory finding: Surface the negative EVA (−14 KRW bn) and explain its strategic implication —
   Samsung SDS's ROC of 8.9% is just below the 9.0% assumed cost of capital, so the company earned
   marginally less than its cost of capital on FY2025 invested capital.
```

Plus in v2.1 §10 *Strategic Recommendations*:

```
Mandatory coverage (driven by negative-EVA finding):

1. Cost-of-capital gap closure (mandatory): Actions to lift RATIO_roc_start from 8.9% above the
   9.0% cost_capital and turn RATIO_eva positive within 24 months. Levers: tactical buybacks
   reducing equity base; deploying cash into higher-return cloud capex; portfolio rationalization
   in Logistics.
```

### Gap explanation

This is the kind of "weird Stage 3 ratio" the Stage 4 brief explicitly calls out as high-value HIL territory. EVA at −14 looks like rounding noise next to positive ROC, ROE, and ROA. It is not noise — it is the substantive finding that Samsung SDS is earning marginally below its 9.0% cost of capital. My v1.0 spec, drafted before populating real numbers, had no mechanism to force the Stage 5 LLM to surface this. A Stage 5 executor reading the v1.0 spec would compute `RATIO_eva` = −14, report it deadpan among the Performance ratios, and probably move on without connecting it to strategic action.

### Why this matters for Stage 5

A spec is not a checklist; it is a contract for what the analysis must address. Burying the most strategically interesting finding inside one numeric cell, without a mandatory clause forcing the executor to confront it, makes the spec a comprehension test for the LLM rather than an instruction set. Rubric criterion 3 ("Clear interpretive guidance; meaningful benchmarks; actionable recommendation criteria") is weakened without this fix. The negative EVA is now wired into three places (flagged finding in §6.1, mandatory finding in §8, mandatory recommendation in §10) so a Stage 5 executor cannot bypass it.

---

## Summary table

| # | Gap (in v1.0) | Fix (in v2.x) | Stage 5 risk if unfixed |
|---|---|---|---|
| 1 | Invented year-suffix named ranges | Aligned to workbook `_curr` / `_prior` convention; added master map §4 | Stage 5 formulas reference non-existent names |
| 2 | Classic 3-component Du Pont | Replaced with 4-component extended form including `RATIO_debt_burden` | Du Pont reconciliation V4 fails silently |
| 3 | Negative EVA had no analytical hook | Added mandatory finding clause in §8 and mandatory recommendation in §10 | Most interesting finding goes unaddressed in Stage 5 |

---

## Iteration discipline note

These three revisions were the consequential ones. Several smaller edits (clarifying tone in §11, adding V8 effective-tax sanity check, V6 share-count rounding reconciliation, the EBIT-vs-NOPAT margin terminology note in §6.3) were applied in the same iteration cycle but are not material enough to warrant separate diff entries. The pattern: when the spec fails the quality test ("could an LLM reconstruct the analysis from this document alone?"), the fix belongs in the spec, not as a hand-edit to the eventual Stage 5 output.
