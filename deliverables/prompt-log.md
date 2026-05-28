---
template: prompt-log
purpose: "Log of meaningful LLM prompt sessions used to draft, iterate, and finalize the Samsung SDS BUS-629 ratios analysis spec"
author: Nguyen Lan Anh
courses: [BUS-629]
stage: 4
spec_file: docs/specs/2026-05-27-nguyen-samsung-sds-spec.md
---

# Prompt Log — BUS-629 AI Ratios Project (Samsung SDS)

This log captures every meaningful LLM session used to draft, iterate, and finalize the technical specification for the Samsung SDS ratio analysis. Each session entry records the model, inputs supplied, prompt intent, output, and the human review actions taken. The HIL notes at the end consolidate the consequential gap-driven revisions across all rounds.

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

## Session 2 — 2026-05-27 | Spec draft (round 1, v1.0)
**Model:** Claude Opus 4.7
**Inputs:** All session-1 inputs plus the four confirmed assumptions.

**Prompt intent:** Using the spec template's structure, draft a technical specification for Samsung SDS accounting ratios analysis. Populate every section (Part A items 1–7, Part B items 8–11). Use named-range notation (`BAL_*`, `INC_*`, `CASH_*`, `RATIO_*`) throughout. Where data values appear in the uploaded Stage 3 workbook, include them numerically in the Data Inputs table. Keep the YAML frontmatter from the template intact.

**Output:** Spec v1.0 saved to `docs/specs/2026-05-27-nguyen-samsung-sds-spec.md`. Covered all eleven required sections. Populated Data Inputs with the nine line items visible in the Stage 2 memo Two-Year Snapshot. Marked the remaining items with `*[TO POPULATE]*` flags. Defined 25 ratios across six categories in named-range notation. Specified a 3-component Du Pont.

**Round-1 gaps identified on review (see HIL Round-1 note below):**
1. Named-range convention invented (`BAL_assets_total_2025` year-suffix style) that did not match the convention actually built into the Stage 3 workbook (`BAL_assets_total_curr` with `_curr`/`_prior` suffix).
2. Du Pont specified as the classic 3-component form (Margin × Asset Turnover × Equity Multiplier); workbook actually implements the **4-component extended** form including `RATIO_debt_burden`.
3. Spec had no dedicated *Named Range Conventions* section even though Part A item 4 requires one.

---

## Session 3 — 2026-05-27 | Round-2 prompt addressing round-1 gaps (v2.0)
**Model:** Claude Opus 4.7

**Prompt intent (verbatim):** *"Review the round-1 draft against the actual Stage 3 workbook screenshots I'm sharing now. Rewrite every named range to use the `_curr` / `_prior` convention used in the workbook (not the year-suffix `_2025` convention you invented). Replace the 3-component Du Pont in §5.6 with the 4-component extended Du Pont actually built into the workbook: `ROE = leverage × asset_turnover × operating_profit_margin × debt_burden`. Then add a new top-level section between Data Inputs and Derived Inputs titled 'Named Range Conventions' — a master map of every named range (BAL_*, INC_*, CFS_*, RATIO_*) to its FY2025 value. Populate every `*[TO POPULATE]*` flag with the actual numeric value from the screenshots. Finally, when you populate the Performance section, flag any ratio output that looks structurally unusual."*

**Output:** Spec v2.0 then v2.1. The named-range rewrite cascaded through Sections 3, 4, 5, 6, and 7 (formulas, validation rules). Du Pont reconciliation in V4 was added explicitly. A new §4 *Named Range Conventions* table covers 21 balance-sheet ranges, 12 income-statement ranges, 20 cash-flow ranges, 5 scalar inputs, 17 derived ranges, and 29 ratio output ranges.

**Weird-ratio finding surfaced during populate-and-flag step:** `RATIO_eva` computed to **−14 KRW bn** despite positive ROC (8.9%) and ROE (8.1%). Drilling in: start-of-year invested capital 10,422 × 9.0% cost of capital = 938, against after-tax operating income of only 924 — a gap of 14 KRW bn. This is not a spec error; it is a substantive finding that Samsung SDS earned marginally below its cost of capital in FY2025. I added a *mandatory finding* clause to §8 and a *mandatory recommendation* clause to §10 so Stage 5 must address this rather than gloss over a small-negative number.

---

## Session 4 — 2026-05-27 | Final polish v2.1 + rubric cross-check
**Model:** Claude Opus 4.7

**Prompt intent:** Cross-check the spec section-by-section against the Stage 4 rubric's *Required spec components* list (Part A items 1–7, Part B items 8–11). Confirm Quality Test prerequisites: could an LLM with zero additional context reconstruct the FY2025 model and produce a substantively correct analysis from this spec alone?

**Output:** Confirmed §1 Scope → §11 Output Format coverage matches all eleven rubric items. Added explicit verification rows V1–V9 in §7. Added presentation conventions in §11 enforcing named-range citation in every Stage 5 numeric assertion (so the spec → analysis traceability chain cannot break). Saved as v2.1, committed to GitHub, fixed Stage 2 memo path reference, granted instructor write access.

---

## Session 5 — 2026-05-28 | Read instructor sweep-review feedback
**Model:** Claude Opus 4.7
**Inputs:** Two instructor review files pulled from PRs on the repo:
- PR #1 — `docs/feedback/stage4-review-2026-05-27.md` (review of the *pre-rebuild* v1.0 spec at `2026-05-26-nguyen-samsung-sds-spec.md`)
- PR #2 — `docs/feedback/stage4-sweep-2026-05-28.md` (post-deadline sweep review of the v2.1 rebuild)

**Prompt intent:** Read both PR review files carefully. Identify the specific improvements the sweep-review flags as the path from the current sweep-bumped score toward 100. For each item, propose a concrete spec edit (file + section + before/after sketch). Do not edit yet — list them for my approval first.

**Output:** Claude returned three substantive items for a v2.2 revision:
1. **Enhanced §6.1 EVA interpretation.** Sweep review quote: *"explicit interpretation guidance on the Performance category EVA finding (why is it negative? what does that signal about Samsung SDS's capital productivity?)"*. Proposed three-reading expansion (capital-productivity gap / over-capitalization / Du Pont reconciliation) plus explicit Stage 5 strategic implication.
2. **More sophisticated §7 Validation Rules.** Sweep review notes the current 9 rules are good but suggests further sophistication. Proposed V10 retained-earnings roll-forward, V11 sign-consistency, V12 quick<current ordering, V13 FCF positivity, V14 net-income reconciliation.
3. **Hypothesis-evaluation framework in §8.** Sweep review quote: *"a hypothesis-evaluation framework anchored to your Stage 2 selection memo's H1/H2/H3"*. Proposed restructure of §8.1 hypotheses into a uniform five-field table per hypothesis (Hypothesis / Operationalization / Test methodology / Result / Strategic implication).

**Secondary item carried forward from PR #1 (original-spec review) where still actionable:** Add specific analytical questions per category in §8 (sharpens the analytical thread). Added as new §8.1.

**My decision:** Approved all three items + the §8.1 carryover. Proceeded to Session 6 to implement.

---

## Session 6 — 2026-05-28 | Spec revisions v2.1 → v2.2
**Model:** Claude Opus 4.7

**Prompt intent:** Implement the four approved items from Session 5. Preserve all existing v2.1 content. Edit the spec surgically — do not rewrite sections that are not touched by these items. Update the version field and changelog block.

**Output:** Spec v2.2 saved at the same path. Changes applied:
- §6.1 — Replaced the one-paragraph "Flagged finding" callout with a structured three-reading interpretation (Reading 1 capital-productivity gap, Reading 2 over-capitalization hypothesis, Reading 3 Du Pont reconciliation) plus explicit Stage 5 strategic implication ("shifts the recommendation set from improve operations to address capital structure").
- §7 — Added V10–V14 to the Validation Rules table with FY2025-computed pass/fail evidence. V10 also includes a Note explaining the 15 KRW bn residual is OCI/equity-method/treasury and pointing Stage 5 to the K-IFRS Statement of Changes in Equity.
- §8 — Added new §8.1 "Specific analytical questions per ratio category" (6 questions, one per category, each tied to a specific named range or §6.1 reading). Restructured the original §8.1 hypothesis block into §8.2 with formal five-field framework for each of H1/H2/H3. Renumbered peer-benchmark table from §8.2 to §8.3.
- Changelog block — Added v2.2 entry summarizing all three sets of changes.
- References — Added explicit pointers to PR #1 and PR #2 review files.

**Round-2 weird-ratio resurfacing:** The V10 retained-earnings roll-forward exposed a small 15 KRW bn residual (0.18%). Rather than absorb this silently, the spec now flags it explicitly with a probable-cause note (OCI from FX translation on the Vietnam logistics affiliate, or treasury stock movement). This is a *minor* finding but it demonstrates the same HIL discipline as the EVA finding — when arithmetic doesn't reconcile to plan, the spec flags it for Stage 5 to investigate rather than hiding it.

---

## HIL Iteration Notes

The HIL discipline ran across three rounds. Each round identified a specific gap and revised either the prompt or the spec to address it. The before/after note below consolidates the three most consequential revisions across rounds 1–3. The Session 5 → Session 6 round (v2.1 → v2.2) is documented in detail in the companion annotated diff at `analysis/validation/2026-05-27-nguyen-samsung-sds-stage4-iteration.md`.

### Round 1 → Round 2 — Three consequential gaps (≈245 words)

**Gap 1 — Wrong naming convention.** My v1.0 spec invented year-suffix named ranges like `BAL_assets_total_2025` and `INC_sales_2025`. After comparing to the Stage 3 workbook screenshots, I found the workbook uses `_curr` / `_prior` suffixes (e.g., `BAL_assets_total_curr`, `BAL_assets_total_prior`) and a year-agnostic naming for income-statement items (`INC_sales`, `INC_ebit`). A Stage 5 LLM fed only my v1.0 spec would have generated ratio formulas referencing names that do not exist in the actual workbook, breaking traceability and silently producing the wrong numbers. **Fix:** rewrote every named range across Sections 3, 4, 5, 6, and 7 to match the workbook's convention exactly.

**Gap 2 — Wrong Du Pont form.** My v1.0 Section 5.6 specified the classic 3-component Du Pont (Margin × Turnover × Equity Multiplier). The workbook actually implements the extended 4-component form including `RATIO_debt_burden = INC_net / NOPAT = 0.847`. Without this fourth term, `RATIO_roe_dupont` would not reconcile to direct ROE (validation V4 would fail). **Fix:** rewrote §6.6 with the four-component formula and added V4 reconciliation tolerance ±0.001.

**Gap 3 — Negative-EVA finding surfaced during populate.** When populating §6.1 with real numbers I noticed `RATIO_eva` = −14 KRW bn — Samsung SDS's ROC (8.9%) is just below its 9.0% cost of capital. This is a Stage-5-level strategic finding hiding inside a tiny ratio. **Fix:** added a *mandatory finding* clause to §8 and a *mandatory recommendation* (cost-of-capital gap closure) to §10 so the Stage 5 executor cannot bypass it.

### Round 3 → Round 4 — Sweep-review response (v2.1 → v2.2, ≈220 words)

After the instructor's sweep review (PR #2, 2026-05-28) confirmed the v2.1 rebuild closed the original-review gaps but called out three further improvements toward 100, I implemented a fourth round of revisions targeting the residual ceiling room.

**Gap 4 — EVA flagged finding was a *number*, not an *interpretation*.** v2.1 stated "EVA = (14)" and asserted the implication but did not show the analytical work that connects the number to a strategic recommendation. A Stage 5 LLM reading v2.1 could report the finding without seeing *why* it matters. **Fix:** restructured the §6.1 callout into a three-reading framework (capital-productivity gap / over-capitalization hypothesis / Du Pont reconciliation) plus an explicit Stage 5 strategic implication clause that reframes the §10 recommendation set from "improve operations" to "address capital structure". Each reading is tied to specific named ranges so Stage 5 cannot summarize without citing the evidence.

**Gap 5 — Validation rules were complete but not *sophisticated*.** V1–V9 covered basic identity and reconciliation; the sweep review noted exemplary specs add cross-statement and sign-consistency checks. **Fix:** added V10–V14 — retained-earnings roll-forward (which itself surfaced a 15 KRW bn OCI residual), sign-consistency, quick<current ordering, FCF positivity, net-income reconciliation. Total now 14 rules.

**Gap 6 — Hypotheses tested but not *framed*.** v2.1 §8.1 listed H1/H2/H3 in narrative bullets. **Fix:** restructured to formal five-field framework per hypothesis, anchoring the analytical thread for Stage 5.

---

## Outstanding items for Stage 5

- **Sources for peer benchmark table** (§8.3): identify FY2025-comparable financials for LG CNS, NAVER Cloud, Accenture, IBM Consulting, TCS, Lotte Information Communication.
- **Segment-level disclosure availability** for H2 test (IT Services vs Logistics asset turnover): confirm with K-IFRS segment note before drafting §4 of the Stage 5 analysis.
- **Share-count precision** for V6 (workbook market cap 14,431 vs back-of-envelope 14,361): pull the exact closing share count from DART filings.
- **FY2024 Income Statement and Cash Flow values** (per PR #1 feedback): source from DART filings to enable two-period margin and CFS trend ratios beyond the current single-year scope.
- **V10 residual decomposition** (15 KRW bn): source K-IFRS Statement of Changes in Equity to decompose the OCI / equity-method / treasury contribution to the retained-earnings reconciliation gap.
