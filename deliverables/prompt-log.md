---
template: prompt-log
purpose: "Log of meaningful LLM prompt sessions used to draft and refine the Samsung SDS BUS-629 ratios analysis spec"
author: Nguyen Lan Anh
courses: [BUS-629]
stage: 4
spec_file: docs/specs/2026-05-27-nguyen-samsung-sds-spec.md
---

# Prompt Log — BUS-629 AI Ratios Project (Samsung SDS)

This log captures the four meaningful LLM sessions used to draft, iterate, and finalize the technical specification for the Samsung SDS ratio analysis. Each session entry records the model, inputs supplied, prompt intent, output, and the human review actions taken. The HIL note at the end consolidates the three most consequential gap-driven revisions.

---

## Session 1 — 2026-05-27 | Assumption elicitation
**Model:** Claude Opus 4.7 (Cowork mode, Claude desktop app)
**Inputs supplied:**
- Stage 4 brief (PDF, uploaded)
- Spec template (`spec-template.md`, raw URL via repo)
- Stage 1 ratios template (`performance-ratios-template.xlsx`)
- Stage 2 selection memo (`2026-05-18-nguyen-samsung-sds-selection.md`)
- Stage 3 populated workbook (`2026-05-21-nguyen-samsung-sds-financials.xlsx`)

**Prompt intent:** Before drafting, ask Claude to surface the three or four assumptions it needed clarified — preventing premature drafting on the wrong premise.

**Output:** Claude returned four assumptions: (a) intended audience for the Stage 5 output, (b) ratio time horizon (single-year vs two-year vs peer-extended), (c) benchmark approach for strategic recommendations, (d) output language.

**My decisions and rationale:**
- **(a) Audience:** Hybrid executive + academic. Matches my professional context as a senior executive at CMC Telecom while satisfying the academic grader.
- **(b) Time horizon:** FY2025 primary, FY2024 only for averaging. Tight scope given two clean years of K-IFRS data; the Stage 3 workbook is built as a single-year analytical model.
- **(c) Benchmarks:** Hypotheses + industry peer combo. Deepens the cross-category criterion in B.8 by stacking a self-reference frame (memo hypotheses) with an external frame (Korean and global IT-services peers).
- **(d) Language:** English only. Spec template is English; grader is US-based; Stage 2 memo is already English.

**Why this session matters:** A one-shot draft without assumption elicitation usually produces a generic spec. By naming the assumptions up front, all downstream content was conditioned on these four choices — not on Claude's defaults.

---

## Session 2 — 2026-05-27 | Spec draft (round 1)
**Model:** Claude Opus 4.7
**Inputs:** All session-1 inputs plus the four confirmed assumptions.

**Prompt intent:** Using the spec template's structure, draft a technical specification for Samsung SDS accounting ratios analysis. Populate every section (Part A items 1–7, Part B items 8–11). Use named-range notation (`BAL_*`, `INC_*`, `CASH_*`, `RATIO_*`) throughout. Where data values appear in the uploaded Stage 3 workbook, include them numerically in the Data Inputs table. Keep the YAML frontmatter from the template intact.

**Output:** Spec v1.0 saved to `docs/specs/2026-05-27-nguyen-samsung-sds-spec.md`. Covered all eleven required sections. Populated Data Inputs with the nine line items visible in the Stage 2 memo Two-Year Snapshot. Marked the remaining items with `*[TO POPULATE]*` flags. Defined 25 ratios across six categories in named-range notation. Specified a 3-component Du Pont.

**Round-1 gaps identified on review (see HIL note below):**
1. Named-range convention invented (`BAL_assets_total_2025` year-suffix style) that did not match the convention actually built into the Stage 3 workbook (`BAL_assets_total_curr` with `_curr`/`_prior` suffix).
2. Du Pont specified as the classic 3-component form (Margin × Asset Turnover × Equity Multiplier); workbook actually implements the **4-component extended** form including `RATIO_debt_burden`.
3. Spec had no dedicated *Named Range Conventions* section even though Part A item 4 requires one.

---

## Session 3 — 2026-05-27 | Round-2 prompt addressing round-1 gaps
**Model:** Claude Opus 4.7

**Prompt intent (verbatim):** *"Review the round-1 draft against the actual Stage 3 workbook screenshots I'm sharing now. Rewrite every named range to use the `_curr` / `_prior` convention used in the workbook (not the year-suffix `_2025` convention you invented). Replace the 3-component Du Pont in §5.6 with the 4-component extended Du Pont actually built into the workbook: `ROE = leverage × asset_turnover × operating_profit_margin × debt_burden`. Then add a new top-level section between Data Inputs and Derived Inputs titled 'Named Range Conventions' — a master map of every named range (BAL_*, INC_*, CFS_*, RATIO_*) to its FY2025 value. Populate every `*[TO POPULATE]*` flag with the actual numeric value from the screenshots. Finally, when you populate the Performance section, flag any ratio output that looks structurally unusual."*

**Output:** Spec v2.0 then v2.1. The named-range rewrite cascaded through Sections 3, 4, 5, 6, and 7 (formulas, validation rules). Du Pont reconciliation in V4 was added explicitly. A new §4 *Named Range Conventions* table covers 21 balance-sheet ranges, 12 income-statement ranges, 20 cash-flow ranges, 5 scalar inputs, 17 derived ranges, and 29 ratio output ranges.

**Weird-ratio finding surfaced during populate-and-flag step:** `RATIO_eva` computed to **−14 KRW bn** despite positive ROC (8.9%) and ROE (8.1%). Drilling in: start-of-year invested capital 10,422 × 9.0% cost of capital = 938, against after-tax operating income of only 924 — a gap of 14 KRW bn. This is not a spec error; it is a substantive finding that Samsung SDS earned marginally below its cost of capital in FY2025. I added a *mandatory finding* clause to §8 and a *mandatory recommendation* clause to §10 so Stage 5 must address this rather than gloss over a small-negative number.

---

## Session 4 — 2026-05-27 | Final polish and rubric cross-check
**Model:** Claude Opus 4.7

**Prompt intent:** Cross-check the spec section-by-section against the Stage 4 rubric's *Required spec components* list (Part A items 1–7, Part B items 8–11). Confirm Quality Test prerequisites: could an LLM with zero additional context reconstruct the FY2025 model and produce a substantively correct analysis from this spec alone?

**Output:** Confirmed §1 Scope → §11 Output Format coverage matches all eleven rubric items. Added explicit verification rows V1–V9 in §7. Added presentation conventions in §11 enforcing named-range citation in every Stage 5 numeric assertion (so the spec → analysis traceability chain cannot break). Saved as v2.1.

---

## HIL Iteration Note — Round 1 → Round 2 (≈245 words)

**Three consequential gaps the round-1 draft contained, and how I revised them.**

**Gap 1 — Wrong naming convention.** My v1.0 spec invented year-suffix named ranges like `BAL_assets_total_2025` and `INC_sales_2025`. After comparing to the Stage 3 workbook screenshots, I found the workbook uses `_curr` / `_prior` suffixes (e.g., `BAL_assets_total_curr`, `BAL_assets_total_prior`) and a year-agnostic naming for income-statement items (`INC_sales`, `INC_ebit`). A Stage 5 LLM fed only my v1.0 spec would have generated ratio formulas referencing names that do not exist in the actual workbook, breaking traceability and silently producing the wrong numbers. **Fix:** rewrote every named range across Sections 3, 4, 5, 6, and 7 to match the workbook's convention exactly.

**Gap 2 — Wrong Du Pont form.** My v1.0 Section 5.6 specified the classic 3-component Du Pont (Margin × Turnover × Equity Multiplier). The workbook actually implements the extended 4-component form including `RATIO_debt_burden = INC_net / NOPAT = 0.847`. Without this fourth term, `RATIO_roe_dupont` would not reconcile to direct ROE (validation V4 would fail). **Fix:** rewrote §6.6 with the four-component formula and added V4 reconciliation tolerance ±0.001.

**Gap 3 — Negative-EVA finding surfaced during populate.** When populating §6.1 with real numbers I noticed `RATIO_eva` = −14 KRW bn — Samsung SDS's ROC (8.9%) is just below its 9.0% cost of capital. This is a Stage-5-level strategic finding hiding inside a tiny ratio. **Fix:** added a *mandatory finding* clause to §8 and a *mandatory recommendation* (cost-of-capital gap closure) to §10 so the Stage 5 executor cannot bypass it.

---

## Outstanding items for future iterations (post-Stage-4)

- **Sources for peer benchmark table** (§8.2): identify FY2025-comparable financials for LG CNS, NAVER Cloud, Accenture, IBM Consulting, TCS, Lotte Information Communication. Stage 5 work.
- **Segment-level disclosure availability** for H2 test (IT Services vs Logistics asset turnover): confirm with K-IFRS segment note before drafting §4 of the Stage 5 analysis.
- **Share-count precision** for V6 (workbook market cap 14,431 vs back-of-envelope 14,361): pull the exact closing share count from DART filings.
