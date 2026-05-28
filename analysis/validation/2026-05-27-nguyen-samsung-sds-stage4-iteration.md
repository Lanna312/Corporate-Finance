---
template: hil-iteration
purpose: "Annotated diff documenting the Stage 4 spec iteration v1.0 → v2.2, gap-by-gap"
author: Nguyen Lan Anh
date: 2026-05-28
company: Samsung SDS Co., Ltd.
ticker: 018260.KS
courses: [BUS-629]
stage: 4
spec_file: docs/specs/2026-05-27-nguyen-samsung-sds-spec.md
companion: deliverables/prompt-log.md
---

# Stage 4 HIL Iteration — Samsung SDS Spec, v1.0 → v2.2 Annotated Diff

This document is the Stage 4 Human-in-the-Loop evidence file (rubric criterion 4 — "Spec craft + prompt log quality"). It accompanies the prompt log and the spec by showing, gap-by-gap, where each LLM draft was wrong, why my spec caused the gap, and what changed in subsequent versions.

Six substantive revisions are documented below across two rounds of HIL iteration. Rounds 1–3 (Iterations 1–3) closed the gaps flagged in the original instructor review (PR #1). Round 4 (Iterations 4–6, v2.1 → v2.2) addresses the remaining ceiling-room toward 100 identified in the instructor sweep review (PR #2).

Each entry follows: **Before** (excerpt) → **After** (excerpt) → **Gap explanation** → **Why this matters for Stage 5**.

---

## ROUND 1 — Initial LLM draft to populated workbook alignment (v1.0 → v2.1)

### Iteration 1 — Named Range Conventions: year-suffix vs `_curr`/`_prior`

#### Before — v1.0 §3 Data Inputs (excerpt)

```
| Named Range                          | FY2024 | FY2025 |
|--------------------------------------|-------:|-------:|
| BAL_assets_total_2024                | 13,238 |        |
| BAL_assets_total_2025                |        | 13,454 |
| INC_sales_2025                       |        | 13,930 |
| BAL_equity_total_2025                |        | 10,263 |
```

#### After — v2.1 §4 Named Range Conventions (excerpt)

```
| Named range                          | FY2024 (prior) | FY2025 (curr) |
|--------------------------------------|---------------:|--------------:|
| BAL_assets_total_*                   |         13,238 |        13,454 |
| BAL_equity_shareholders_*            |          9,705 |        10,263 |
| INC_sales                            |              — |        13,930 |

> Replace `*` with `curr` for FY2025 or `prior` for FY2024.
```

#### Gap explanation

The Stage 3 workbook uses `_curr` / `_prior` suffixes for balance-sheet items (year-agnostic, reusable) and no suffix for income-statement items (since IS is single-year only in the workbook). My v1.0 spec invented a year-suffix convention (`_2024`, `_2025`) that does not exist anywhere in the workbook. A Stage 5 LLM fed only the spec would generate formulas referencing names that don't resolve — or worse, look correct in isolation but mismatch the actual workbook structure.

#### Why this matters for Stage 5

The whole point of the spec is to let an LLM with no prior context reproduce the analysis. If named ranges in the spec don't match the workbook, the spec breaks its own quality test. Rubric criterion 1 ("Every input value present numerically; architecture fully defined") is unearnable without this fix.

---

### Iteration 2 — Du Pont decomposition: 3-component → 4-component extended

#### Before — v1.0 §5.6 Du Pont Decomposition

```
**5.6 Du Pont Decomposition (3-step)**

| Component                  | Named Range                  | Formula                                     |
|----------------------------|------------------------------|---------------------------------------------|
| Net Margin                 | RATIO_dupont_net_margin_2025 | INC_net_income_2025 / INC_sales_2025        |
| Asset Turnover             | RATIO_dupont_at_2025         | INC_sales_2025 / BAL_assets_total_avg_2025  |
| Equity Multiplier          | RATIO_dupont_em_2025         | BAL_assets_total_avg / BAL_equity_total_avg |
| ROE Du Pont                | RATIO_roe_dupont_2025        | Margin × Turnover × Equity Multiplier       |
```

#### After — v2.1 §6.6 Du Pont System (4-component extended)

```
| Component                       | Named range                     | Formula                                                                                              | FY2025 |
|---------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------|-------:|
| ROA (Du Pont)                   | RATIO_roa_dupont                | RATIO_asset_turnover × RATIO_operating_profit_margin                                                  |   7.0% |
| ROE (Du Pont, extended)         | RATIO_roe_dupont                | RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden             |   7.8% |
```

#### Gap explanation

The Stage 3 workbook implements the **extended** (4-component) Du Pont:
- `RATIO_leverage` = `currentYear_assets_total` / `currentYear_equity` = 1.31x
- `RATIO_asset_turnover` = `INC_sales` / `startYear_total_assets` = 1.05x
- `RATIO_operating_profit_margin` = NOPAT / `INC_sales` = 6.6%
- `RATIO_debt_burden` = `INC_net` / NOPAT = 0.847

Product: 1.31 × 1.05 × 0.066 × 0.847 = **7.78%** ≈ workbook ROE (avg) of 7.8% ✓

The classic 3-component Du Pont (Margin × Turnover × Equity Multiplier) would have given 5.6% × 1.05 × 1.31 = 7.7%, close numerically but using `RATIO_profit_margin` (net) instead of `RATIO_operating_profit_margin` (NOPAT) × `RATIO_debt_burden`. The 4-component form decomposes the after-interest impact via `RATIO_debt_burden` — a richer analytical decomposition that the workbook author chose deliberately.

#### Why this matters for Stage 5

Stage 5 §7 (Du Pont Decomposition) must reconcile component-by-component back to direct ROE. A 3-component spec would force the executor to either ignore `RATIO_debt_burden` (failing reconciliation) or re-derive a different formula (defeating the purpose of having a spec). Rubric criterion 2 ("All 25+ ratios with correct formulas in named-range notation") and Validation Rule V4 (Du Pont reconciliation) both depend on this fix.

---

### Iteration 3 — Negative EVA finding: from oversight to mandatory analysis requirement

#### Before — v1.0 §5.1 Performance (excerpt)

```
| Ratio                   | Named Range          | Formula                                                                                |
|-------------------------|----------------------|-----------------------------------------------------------------------------------------|
| Economic Value Added    | RATIO_eva_2025       | INC_nopat_2025 − (BAL_capital_invested_avg_2025 × WACC_2025)                            |
```

(No flag, no value, no analytical guidance. Just a formula.)

#### After — v2.1 §6.1 Performance (excerpt) + cross-references in §8 and §10

```
| Ratio                   | Named range                     | FY2025  |
|-------------------------|---------------------------------|--------:|
| Economic value added    | RATIO_eva                       | **(14)** |

> Flagged finding: EVA is slightly negative (−14 KRW bn) despite positive ROC of 8.9%, because the start-of-year invested capital of 10,422 multiplied by the 9.0% cost of capital (938) exceeds the after-tax operating income of 924. Stage 5 must address this in §8 and §10.
```

#### Gap explanation

This is the kind of "weird Stage 3 ratio" the Stage 4 brief explicitly calls out as high-value HIL territory. EVA at −14 looks like rounding noise next to positive ROC, ROE, and ROA. It is not noise — it is the substantive finding that Samsung SDS is earning marginally below its 9.0% cost of capital. My v1.0 spec, drafted before populating real numbers, had no mechanism to force the Stage 5 LLM to surface this. A Stage 5 executor reading the v1.0 spec would compute `RATIO_eva` = −14, report it deadpan among the Performance ratios, and probably move on without connecting it to strategic action.

#### Why this matters for Stage 5

A spec is not a checklist; it is a contract for what the analysis must address. Burying the most strategically interesting finding inside one numeric cell, without a mandatory clause forcing the executor to confront it, makes the spec a comprehension test for the LLM rather than an instruction set. Rubric criterion 3 ("Clear interpretive guidance; meaningful benchmarks; actionable recommendation criteria") is weakened without this fix.

---

## ROUND 2 — Sweep-review response (v2.1 → v2.2)

The instructor's sweep review (PR #2, 2026-05-28) confirmed the v2.1 rebuild closed the original-review gaps but identified ceiling room toward 100. Iterations 4–6 below address each item.

### Iteration 4 — EVA flagged finding: from *number* to *interpretation*

#### Before — v2.1 §6.1 EVA callout

```
> **Flagged finding:** EVA is slightly negative (−14 KRW bn) despite positive ROC of 8.9%, because the start-of-year invested capital of 10,422 multiplied by the 9.0% cost of capital (938) exceeds the after-tax operating income of 924. Stage 5 must address this in §8 and §10.
```

(Single paragraph. States the finding, asserts the implication, points downstream. Does not show the analytical work that connects the arithmetic to a strategic recommendation.)

#### After — v2.2 §6.1 EVA callout (three-reading framework)

```
> **Flagged finding — strategic interpretation (mandatory for Stage 5):**
>
> EVA is slightly negative (−14 KRW bn) despite positive ROC of 8.9%. The arithmetic:
> startYear_total_capitalization (10,422) × cost_capital (9.0%) = 938 >
> currentYear_after_tax_operating_income (924) — a 14 KRW bn marginal value-destruction
> signal. Three readings the Stage 5 analysis must resolve:
>
> Reading 1 — Capital-productivity gap. Samsung SDS earns 0.1 percentage points below
> its 9.0% cost of capital. For a KRW 14.4 trillion market-cap firm, this signals returns
> roughly at — but not above — the marginal hurdle investors require...
>
> Reading 2 — Over-capitalization hypothesis. Three signals stack: (i) RATIO_leverage =
> 1.31x is well below IT-services peer norms of 1.8–2.5x; (ii) currentYear_cash... = 6,380
> represents 47% of currentYear_assets_total (13,454); (iii) RATIO_eva is negative.
> Together these suggest the equity base is too large relative to value-creating
> opportunities...
>
> Reading 3 — Du Pont reconciliation. RATIO_roe_avg of 7.8% sits below the 9.0%
> cost_capital. The 4-component Du Pont decomposition (§6.6) reveals RATIO_leverage
> (1.31x) is the binding constraint... ROE would clear 9.0% if leverage rose to ~1.55x
> with everything else held constant.
>
> Stage 5 strategic implication: The negative-EVA finding shifts the recommendation set
> from "improve operations" to "address capital structure". Tactical buybacks, special
> dividends, or productive deployment of the KRW 6.4 trn cash position are the highest-NPV
> levers — not operating efficiency.
```

#### Gap explanation

Sweep review quote: *"explicit interpretation guidance on the Performance category EVA finding (why is it negative? what does that signal about Samsung SDS's capital productivity?)"*. The v2.1 callout stated the finding but did not unpack it. A Stage 5 LLM could read v2.1 and produce a one-sentence acknowledgement ("EVA is negative, suggesting returns are below cost of capital") without engaging with the three substantively distinct interpretations. The v2.2 callout forces engagement: each reading is tied to specific named ranges so the Stage 5 narrative cannot summarize without citing the evidence, and the strategic implication clause explicitly directs §10 recommendations toward capital structure rather than operations.

#### Why this matters for Stage 5

This is criterion 3 ("Clear interpretive guidance") and criterion 4 ("Specific, actionable critique") territory. The three-reading framework operates as both interpretive guidance for §2 of the Stage 5 output and as a structural constraint on §9's strategic recommendations. Without it, Stage 5 would produce generic "improve operating efficiency" recommendations that miss the real lever.

---

### Iteration 5 — Validation Rules: from *complete* to *sophisticated* (V10–V14)

#### Before — v2.1 §7 Validation Rules

Nine rules: V1 (BS balance FY2025), V2 (BS balance FY2024), V3 (Du Pont ROA reconciliation), V4 (Du Pont ROE reconciliation), V5 (Cash Flow reconciliation), V6 (Market cap derivation), V7 (Memo cross-check), V8 (Effective tax sanity), V9 (Negative-denominator guard).

All identity / reconciliation / sanity checks. No cross-statement business-logic checks. No sign-consistency assertions. No ratio-ordering assertions.

#### After — v2.2 §7 Validation Rules (V10–V14 added)

```
| V10 | Retained earnings roll-forward | BAL_retained_earnings_prior + (INC_net − INC_dividends) ≈ BAL_retained_earnings_curr (tolerance ±50 KRW bn for treasury / other equity adjustments) | 7,995 + (783 − 233) = 8,545 vs 8,530 → Δ = 15 KRW bn (0.18%) ✓ |
| V11 | Sign-consistency — Operating profitability | Sign(INC_ebit) = Sign(RATIO_operating_profit_margin) = Sign(RATIO_roa_start) | + = + = + ✓ |
| V12 | Liquidity ordering (Quick ≤ Current) | RATIO_quick ≤ RATIO_current (always true if BAL_inventories_curr ≥ 0) | 3.85x ≤ 4.03x ✓ |
| V13 | Free Cash Flow positivity | CFS_operating − ABS(CFS_capex) > 0 (FCF before financing) | 1,061 − 386 = 675 > 0 ✓ |
| V14 | Net-income-to-retained-earnings reconciliation | INC_net ≈ INC_dividends + INC_addition_retained_earnings (tolerance ±0.5 KRW bn) | 783 = 233 + 550 = 783 ✓ |
```

Plus a Note explaining the V10 15 KRW bn residual is attributable to other comprehensive income (FX translation on overseas subsidiaries, primarily Vietnam logistics affiliate), equity-method gains/losses, or treasury stock movement — and pointing Stage 5 to the K-IFRS Statement of Changes in Equity for precise decomposition.

#### Gap explanation

Sweep review quote: *"more sophisticated validation rules (currently 9 — exemplary specs in the cohort have 9+ with computed expected values; you have this)"*. The v2.1 rules were structurally complete (identity + reconciliation + sanity) but did not include the second tier of cross-statement business-logic checks that catch subtle errors in real-world filings. V10 in particular surfaces a 0.18% residual that points at a real economic phenomenon (OCI / equity-method / treasury) rather than at a model defect — turning a validation rule into a finding.

#### Why this matters for Stage 5

Rubric criterion 2 ("Ratios & Validation") grades validation depth alongside ratio coverage. Stage 5's manual verification table (10% of Stage 5) will compare LLM output to source data; if the spec contains sophisticated validation rules, Stage 5 can use them as checks rather than re-deriving the same logic. The V10 residual specifically gives Stage 5 a substantive finding to investigate (the Vietnam-affiliate FX translation hypothesis) that connects back to my own professional context at CMC Telecom.

---

### Iteration 6 — Hypotheses: from *bullets* to *framework*

#### Before — v2.1 §8.1 Hypothesis bullets

```
**8.1 Hypotheses to test (from Stage 2 memo)**

- **H1 Profitability** — Operating margin expands from 6.6% (FY2024) toward 6.8–7.2%
  (FY2025) driven by higher-margin cloud / digital-transformation mix. **Test:**
  INC_ebit / INC_sales = 6.9% lies inside 6.8–7.2% → **H1 confirmed**. Stage 5 must note
  that workbook's RATIO_operating_profit_margin (NOPAT-based, 6.6%) is a different
  construct than memo's EBIT margin.
- **H2 Efficiency** — IT Services segment asset turnover exceeds Logistics segment
  asset turnover in FY2025. **Test:** segment disclosures from K-IFRS filings; if
  segment data unavailable, perform narrative-only assessment and note the limitation
  explicitly.
- **H3 Liquidity** — Current ratio remains above 3.8x–4.0x in FY2025. **Test:**
  RATIO_current = 4.03x exceeds 4.0x → **H3 confirmed**.
```

Three bulleted hypotheses, each with test methodology embedded inline. No uniform structure across the three. No explicit "strategic implication" field.

#### After — v2.2 §8.2 Formal five-field framework (H1 excerpt)

```
**H1 — Profitability (margin expansion via cloud/digital-transformation business mix)**

| Field | Detail |
|---|---|
| Hypothesis | Operating margin expands from 6.6% (FY2024) toward 6.8–7.2% (FY2025) driven by higher-margin cloud and digital-transformation revenue share growing faster than total revenue. |
| Operationalization | EBIT margin = INC_ebit / INC_sales. Note: Workbook's RATIO_operating_profit_margin is NOPAT-based (6.6%) — different construct, must be labeled separately. |
| Test methodology | Compute INC_ebit (957) / INC_sales (13,930) = 6.87%, compare to the memo's FY2024 6.6% baseline and to the 6.8–7.2% expected band. |
| Result | 6.87% lies inside the 6.8–7.2% band, expanded ~30 bps YoY → **H1 confirmed**. |
| Strategic implication | Mix shift is operating but at the low end of the expected band — suggests cloud growth is real but not yet accelerating disproportionately. Stage 5 should test FY2026 trajectory: is cloud revenue share accelerating or decelerating? The §10 business-mix recommendation depends on this directional read. |
```

(H2 and H3 follow the same structure. H3's *Strategic implication* row links explicitly to §6.1 EVA reading: "The cash-rich structure is confirmed, *but* the §6.1 EVA finding suggests this liquidity is not earning its cost...This tension is the central strategic question of the entire analysis.")

#### Gap explanation

Sweep review quote: *"a hypothesis-evaluation framework anchored to your Stage 2 selection memo's H1/H2/H3"*. The v2.1 bullets were *adequate* — they stated the hypothesis, the test, and the result — but they were not a *framework*. A framework imposes uniform structure that exposes the comparable strategic implications across the three hypotheses. The v2.2 five-field structure (Hypothesis / Operationalization / Test methodology / Result / Strategic implication) achieves this and explicitly bridges H3's confirmation to the §6.1 EVA finding — turning the three hypothesis tests into a single coherent narrative arc rather than three isolated checks.

#### Why this matters for Stage 5

Criterion 3 ("Analysis spec") and criterion 4 ("Spec craft") both reward structural sophistication. The five-field framework forces Stage 5 to populate the Strategic Implication row for each hypothesis — preventing the common failure mode where a Stage 5 LLM confirms each hypothesis arithmetically but does not articulate what the confirmations *mean for the executive reader*.

---

## Bonus iteration — §8.1 Specific analytical questions per category

Carried forward from the original PR #1 review item: *"Add one specific analytical question per category in Section 8."*

v2.1 had no per-category anchoring questions. v2.2 adds §8.1 with six sharp questions, one per category, each tied to a specific named range or §6.1 reading. Example for the Leverage category:

> **Leverage** — At `RATIO_long_term_debt_equity` of 0.05x, is Samsung SDS preserving optionality for future M&A and capital-flexible strategic moves, or is it leaving financial-engineering value on the table (per the §6.1 over-capitalization reading)?

These questions anchor the analytical thread for Stage 5 — moving the narrative from descriptive ("the current ratio is high") to interpretive ("is the current ratio signaling strength or signaling inefficient deployment?").

---

## Summary table — six iterations across two rounds

| # | Round | Gap (in prior version) | Fix (in next version) | Stage 5 risk if unfixed |
|---|---|---|---|---|
| 1 | R1 (v1.0→v2.x) | Invented year-suffix named ranges | Aligned to workbook `_curr` / `_prior` convention; added master map §4 | Stage 5 formulas reference non-existent names |
| 2 | R1 | Classic 3-component Du Pont | Replaced with 4-component extended form including `RATIO_debt_burden` | Du Pont reconciliation V4 fails silently |
| 3 | R1 | Negative EVA had no analytical hook | Added mandatory finding clause in §8 and mandatory recommendation in §10 | Most interesting finding goes unaddressed in Stage 5 |
| 4 | R2 (v2.1→v2.2) | EVA flagged but not interpreted | Three-reading framework (capital-productivity / over-capitalization / Du Pont) + Stage 5 strategic implication clause | Stage 5 reports the finding generically; misses the "address capital structure not operations" reframe |
| 5 | R2 | Validation rules complete but not sophisticated | Added V10–V14 (retained-earnings roll-forward, sign-consistency, quick<current, FCF positivity, NI reconciliation) | Stage 5 manual verification (10%) misses the V10 OCI residual finding |
| 6 | R2 | Hypotheses bulleted, not framed | Restructured to formal five-field framework per H1/H2/H3 with explicit Strategic Implication field | Hypothesis confirmations become isolated arithmetic checks rather than a strategic narrative arc |

---

## Iteration discipline note

These six revisions were the consequential ones. Several smaller edits were applied in the same iteration cycles but are not material enough to warrant separate diff entries: clarifying tone in §11, V6 share-count rounding reconciliation, the EBIT-vs-NOPAT margin terminology note in §6.3, the new §8.1 anchoring questions (documented in the Bonus iteration above), and updated References pointers to PR #1 and PR #2 review files.

The pattern across both rounds: when the spec fails the quality test ("could an LLM reconstruct the analysis from this document alone?"), the fix belongs in the spec, not as a hand-edit to the eventual Stage 5 output. Each iteration above lifts the spec's *self-containment* — the property the rubric calls out as the test of spec craft.
