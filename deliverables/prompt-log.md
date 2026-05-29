---
template: prompt-log
purpose: "Log of meaningful LLM prompt sessions used to draft, iterate, and finalize the Samsung SDS BUS-629 ratios analysis spec and the Stage 5 analysis built from it"
author: Nguyen Lan Anh
courses: [BUS-629]
stages: [4, 5]
spec_file: docs/specs/2026-05-27-nguyen-samsung-sds-spec.md
stage5_files:
  - deliverables/2026-05-28-nguyen-samsung-sds-llm-raw.md
  - analysis/validation/2026-05-28-nguyen-samsung-sds-stage5-verification.md
  - deliverables/2026-05-28-nguyen-samsung-sds-final-analysis.md
  - deliverables/2026-05-28-nguyen-samsung-sds-spec-retrospective.md
---

# Prompt Log — BUS-629 AI Ratios Project (Samsung SDS)

This log captures every meaningful LLM session used to draft, iterate, and finalize the technical specification for the Samsung SDS ratio analysis (Stage 4) and to execute the analysis itself (Stage 5). Each session entry records the model, inputs supplied, prompt intent, output, and the human review actions taken. The HIL notes consolidate the consequential gap-driven revisions across all rounds.

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
- **(a) Audience:** Hybrid executive + academic.
- **(b) Time horizon:** FY2025 primary, FY2024 only for averaging.
- **(c) Benchmarks:** Hypotheses + industry peer combo.
- **(d) Language:** English only.

---

## Session 2 — 2026-05-27 | Spec draft (round 1, v1.0)
**Model:** Claude Opus 4.7
**Inputs:** All session-1 inputs plus the four confirmed assumptions.

**Prompt intent:** Using the spec template's structure, draft a technical specification for Samsung SDS accounting ratios analysis. Populate every section. Use named-range notation throughout. Include numeric values from the Stage 3 workbook. Keep YAML frontmatter intact.

**Output:** Spec v1.0 saved. Covered all eleven required sections. Round-1 gaps identified: invented year-suffix named ranges, classic 3-component Du Pont, no dedicated Named Range Conventions section.

---

## Session 3 — 2026-05-27 | Round-2 prompt addressing round-1 gaps (v2.0)
**Model:** Claude Opus 4.7

**Prompt intent (verbatim):** *"Review the round-1 draft against the actual Stage 3 workbook screenshots I'm sharing now. Rewrite every named range to use the `_curr` / `_prior` convention used in the workbook. Replace the 3-component Du Pont in §5.6 with the 4-component extended Du Pont. Add a top-level Named Range Conventions section. Populate every TO POPULATE flag with actual numeric values. Flag any ratio output that looks structurally unusual."*

**Output:** Spec v2.0 then v2.1. Named-range rewrite cascaded through Sections 3, 4, 5, 6, 7. New §4 master map. Du Pont reconciliation V4 added.

**Weird-ratio finding:** `RATIO_eva` = −14 KRW bn surfaced during populate. Added mandatory finding clause to §8 and mandatory recommendation clause to §10.

---

## Session 4 — 2026-05-27 | Final polish v2.1 + rubric cross-check
**Model:** Claude Opus 4.7

**Prompt intent:** Cross-check the spec section-by-section against the Stage 4 rubric. Confirm Quality Test prerequisites.

**Output:** Confirmed all eleven rubric items covered. Saved as v2.1, committed to GitHub, fixed Stage 2 memo path reference, granted instructor write access.

---

## Session 5 — 2026-05-28 | Read instructor sweep-review feedback
**Model:** Claude Opus 4.7
**Inputs:** Two instructor review files from PRs on the repo (PR #1 original review of v1.0; PR #2 sweep review of v2.1).

**Prompt intent:** Read both PR review files carefully. Identify the specific improvements the sweep-review flags as the path toward 100. For each item, propose a concrete spec edit. Do not edit yet — list for approval first.

**Output:** Claude returned three substantive items for v2.2 revision: enhanced EVA interpretation, more sophisticated validation rules, hypothesis-evaluation framework. Plus carryover item from PR #1: specific analytical questions per category.

**My decision:** Approved all four items. Proceeded to Session 6.

---

## Session 6 — 2026-05-28 | Spec revisions v2.1 → v2.2
**Model:** Claude Opus 4.7

**Prompt intent:** Implement the four approved items from Session 5. Preserve all existing v2.1 content. Edit surgically. Update version field and changelog block.

**Output:** Spec v2.2 saved. Changes applied:
- §6.1 — Replaced one-paragraph "Flagged finding" with structured three-reading interpretation (capital-productivity gap / over-capitalization hypothesis / Du Pont reconciliation) plus explicit Stage 5 strategic implication.
- §7 — Added V10–V14 to Validation Rules. V10 surfaced 15 KRW bn OCI residual.
- §8 — Added §8.1 "Specific analytical questions per ratio category" (6 questions). Restructured §8.1 hypothesis block into §8.2 with formal five-field framework. Renumbered peer-benchmark to §8.3.
- Changelog: Added v2.2 entry.
- References: Added pointers to PR #1 and PR #2 review files.

---

## Session 7 — 2026-05-28 | Read Stage 5 brief and plan execution
**Model:** Claude Opus 4.7
**Inputs supplied:** Stage 5 brief from instructor's GitHub.

**Prompt intent:** Read the Stage 5 brief carefully. Identify six deliverables, suggested production order, and rubric weighting. Plan the Stage 5 workflow accordingly.

**Output:** Detailed Stage 5 plan covering raw LLM output, manual verification, final analysis, spec retrospective, prompt log update, and repo polish pass.

---

## Session 8 — 2026-05-28 | Produce Stage 5 raw LLM output (cold-context simulation)
**Model:** Claude Opus 4.7

**Prompt intent (cold-context simulation per Stage 5 brief Step 2):** *"Read the attached technical specification and produce the full ratio analysis it instructs you to produce. Follow §11 Output Format exactly. Cite named ranges per the spec's presentation conventions. Do not consult any external data or prior context."*

**Inputs supplied:** **Spec v2.2 only.**

**Output:** Raw LLM output saved unedited to `deliverables/2026-05-28-nguyen-samsung-sds-llm-raw.md`. Approximately 10-12 pages rendered. Structure followed §11 Output Format exactly.

**Notable LLM behaviors observed:**
- Named-range citation discipline honored throughout.
- EVA three-reading framework reproduced with high fidelity.
- H2 correctly listed as TBD pending segment data; no fabrication.
- Du Pont 4-component identified `RATIO_leverage` as binding constraint and produced 1.55x sensitivity unprompted.
- DSO compression target set at 55 days (later domain-corrected in final analysis).

---

## Session 9 — 2026-05-28 | Manual ratio verification
**Model:** Claude Opus 4.7 (used as computational verification assistant)

**Prompt intent:** Recompute seven ratios from Stage 3 financial data using full-decimal precision. Compare to Session 8 LLM raw output values. Flag and explain any discrepancies.

**Output:** Saved as `analysis/validation/2026-05-28-nguyen-samsung-sds-stage5-verification.md`. Seven ratios verified across all six categories. All seven match LLM-stated values within rounding tolerance.

**Headline finding:** the match-rate is meaningful — it demonstrates spec named-range specificity successfully constrained LLM output. DSO row, EVA row, and Du Pont row are the most informative because they show where LLM *could* have diverged and spec prevented divergence.

**Substantive verification observation:** Du Pont V4 reconciliation passes with full-decimal precision but is at-boundary with displayed 2-decimal precision. Real spec gap — captured in retrospective Gap 1.

---

## Session 10 — 2026-05-28 | Build evaluated final analysis (initial pass — cold-context-LLM-plus-light-domain-knowledge)
**Model:** Claude Opus 4.7

**Prompt intent:** Build the Stage 5 final analysis by integrating raw LLM output, manual verification findings, and author domain knowledge (CMC Telecom International Business Director, Vietnam/SE-Asia regional context, Samsung Group ecosystem familiarity). Add an explicit "LLM Evaluation & Annotations" section. Add an "Executive Justification" section in author voice.

**Output:** Initial final analysis saved as `deliverables/2026-05-28-nguyen-samsung-sds-final-analysis.md`. Approximately 14–15 pages. Three domain corrections logged: DSO target 55 → 58 days, CMC Corporation Vietnam-platform-as-anchor framing for Recommendation 2, Samsung Group risk posture context for Leverage.

---

## Session 11 — 2026-05-28 | Build spec retrospective (initial pass)
**Model:** Claude Opus 4.7

**Prompt intent:** Produce a structured retrospective on spec v2.2 using the Stage 5 LLM execution as empirical feedback. Follow the template structure: section-by-section verdict, top 3 gaps with evidence, 3 revisions, effectiveness rating, forward link, process feedback.

**Output:** Initial retrospective saved. Top 3 gaps: V4 reconciliation precision, §10 author-domain-correction handling, §8.2 H2 narrative fallback methodology. Effectiveness rating: 4 of 5.

---

## Session 12 — 2026-05-28 | Personalization revision — integrate Samsung SDS strategic and operating context
**Model:** Claude Opus 4.7

**Prompt intent (verbatim):** *"Keep the LLM raw output file unchanged. Revise the other four files (verification, final analysis, spec retrospective, prompt log) in my personalized professional voice — chuyên nghiệp, tỉ mỉ, rõ ràng. Add the Samsung SDS strategic and operating context I have from professional experience: (i) Samsung SDS is the ICT services arm of the Samsung Group; (ii) approximately 80% of revenue is generated from intra-group Samsung affiliate work, with ~20% external — moderate margins are an outcome of intra-group transfer pricing; (iii) the firm has been pushing external customer growth for the past 3 years with modest progress because internal Samsung affiliate demand is large; (iv) segment composition is Data Center, Cloud, IT Outsourcing (ITO), Digital Transformation (DX) — analyze how segment mix affects financial performance; (v) Samsung SDS is the largest shareholder of CMC Corporation in Vietnam since 2019 (strategic investor; CMC Telecom is the author's employer); (vi) Samsung SDS operates Global Delivery Centers in Vietnam, India, and China to reduce ITO cost-of-delivery and lift margins."*

**Output revision plan:**
- **LLM raw file:** UNCHANGED per instruction.
- **Verification table:** Light additions in the Notes column for Row 2 (DSO) and Row 3 (EVA) integrating the intra-group revenue mix and Samsung Group value capture context. Two new Observations added (Observation 3 on DSO interpretation context, Observation 4 on Samsung Group value capture). Headline preserved.
- **Final analysis:** Substantial rewrite. New §1.2 Revenue mix and ratio implications table. New §1.3 External customer growth strategic push context. New §1.4 Samsung SDS Vietnam strategy (CMC majority stake + GDC network). EVA framework expanded to four readings — Reading 4 on Samsung Group consolidated value capture added. H1 strategic implication refined to flag segment-mix-driven (not pricing-driven) margin lift. DSO compression target revised one more time from 58 → 62 days based on the ~80% intra-group constraint. Recommendation 2 reframed from "explore Vietnam / SE-Asia M&A" to "scale existing CMC majority-stake position and GDC network." Recommendation 1 internal framing reworked as Samsung Group treasury coordination. §5 LLM Evaluation now logs four domain corrections (originally three). §7 Executive Justification reworked to lead with the strategic / operating thesis.
- **Spec retrospective:** New §3 Data Inputs entry flagged "Missing revenue-mix context — see Gap 10 below." New Gap 10 expanded treatment in §7: proposed §3.5 "Revenue mix and strategic operating context" subsection for v2.4 spec, with six rows capturing intra-group revenue share, external customer share, segment composition, Samsung Group treasury policy, Vietnam strategic positioning, GDC network. Effectiveness rating maintained at 4 of 5 — rationale: Gap 10 surfaced *during* Stage 5 production rather than *before* it, so a v2.2 author could not have anticipated it without running the cold-context test.
- **Prompt log:** This entry (Session 12).

**Why this session matters.** The cold-context LLM produced an analytically correct draft. The strategic and operating context — revenue mix, segment composition, group treasury policy, regional positioning — is what turns a correct ratio analysis into an executive-grade financial briefing. This session is the embodiment of the Stage 5 workflow the BUS-629 course is teaching: the LLM proposes, the author refines, and the refinement is grounded in company-specific context the LLM cannot have. The four domain corrections logged in the final analysis §5.2 — DSO 55→62 days, Recommendation 2 reframing, Samsung Group treasury context, EVA Reading 4 — are the deliverable's strongest single demonstration of domain-knowledge value-add over LLM-only output.

---

## HIL Iteration Notes

The HIL discipline ran across five rounds. Each round identified specific gaps and revised either the prompt or the spec to address them. The before/after notes below consolidate the most consequential revisions.

### Round 1 → Round 2 — Three consequential gaps (≈245 words)

**Gap 1 — Wrong naming convention.** My v1.0 spec invented year-suffix named ranges. Workbook uses `_curr` / `_prior` suffixes and year-agnostic IS naming. **Fix:** rewrote every named range across Sections 3, 4, 5, 6, 7 to match workbook convention.

**Gap 2 — Wrong Du Pont form.** v1.0 specified classic 3-component; workbook implements extended 4-component including `RATIO_debt_burden`. **Fix:** rewrote §6.6 with four-component formula; added V4 reconciliation tolerance.

**Gap 3 — Negative-EVA finding surfaced during populate.** −14 KRW bn — Samsung SDS earns just below cost of capital. Stage-5-level strategic finding. **Fix:** added mandatory finding clause to §8 and mandatory recommendation to §10.

### Round 3 → Round 4 — Sweep-review response (v2.1 → v2.2, ≈220 words)

**Gap 4 — EVA flagged finding was a *number*, not an *interpretation*.** **Fix:** restructured §6.1 callout into three-reading framework plus explicit Stage 5 strategic implication clause.

**Gap 5 — Validation rules complete but not *sophisticated*.** **Fix:** added V10–V14 (retained-earnings roll-forward — surfaced 15 KRW bn OCI residual, sign-consistency, quick<current ordering, FCF positivity, NI reconciliation).

**Gap 6 — Hypotheses tested but not *framed*.** **Fix:** restructured to formal five-field framework per H1/H2/H3.

### Round 5 — Stage 5 cold-context execution surfaced three new gaps (~180 words)

**Gap 7 — V4 Du Pont reconciliation precision.** V4 tolerance ±0.001 at-boundary with displayed 2-decimal precision. **v2.3 fix:** explicit precision-statement in V4.

**Gap 8 — Domain-correction handling.** §10 has no clause anticipating author-domain corrections to LLM-proposed recommendations. **v2.3 fix:** sixth recommendation criterion and §11 "Domain corrections" subsection requirement.

**Gap 9 — §8.2 H2 fallback methodology.** Spec instructs "narrative-only assessment using peer proxies" without ranges. **v2.3 fix:** provide bracketing ranges (IT-services AT 1.1–1.3x; Logistics-services AT 0.6–0.9x).

### Round 6 — Personalization revision surfaced one substantial new gap (≈200 words)

**Gap 10 — Revenue-mix and strategic operating context missing from §3 Data Inputs.** Spec captures financial data but does not capture revenue-mix structure (intra-group ~80% / external ~20%), segment composition (Data Center / Cloud / ITO / DX), Samsung Group treasury policy, Vietnam strategic positioning (CMC majority stake; GDC network in Vietnam / India / China). A cold-context LLM lacking this context produces analytically correct but interpretively shallow output. Four substantive interpretive moves in the final analysis required this context: DSO compression target (55 → 62 days through layered refinement), EVA Reading 4 (Samsung Group consolidated value capture), Recommendation 2 reframing (from "explore" to "scale existing platform"), Recommendation 1 internal framing (Samsung Group treasury coordination). **v2.4 fix:** add §3.5 "Revenue mix and strategic operating context" subsection with six rows capturing the missing context, estimated effort 30–45 minutes including K-IFRS related-party verification. See spec retrospective §7 for full expanded treatment.

The pattern across all six rounds: when the spec fails its quality test in some way, the fix belongs in the spec, not as a hand-edit to the eventual Stage 5 output. Each round above lifts the spec's self-containment — the property the rubric calls out as the test of spec craft.

---

## Outstanding items (post-Stage-5)

- **v2.3 spec revision sweep.** Three surgical edits (~45 minutes) closing Gaps 7–9. Could be made during Stage 5 polish or deferred to portfolio-quality pass.
- **v2.4 spec revision.** Add §3.5 "Revenue mix and strategic operating context" subsection closing Gap 10 (~30–45 minutes). Most impactful single spec improvement available.
- **FY2024 IS and CFS sourcing** from DART filings — for two-period margin and CFS trend analysis.
- **K-IFRS Segment Note** from FY2025 DART filing — to resolve H2 hypothesis with actual segment data.
- **K-IFRS related-party disclosure note** — to confirm or refine the 80/20 intra-group vs external revenue mix estimate.
- **Live peer benchmark data** — LG CNS, NAVER Cloud, Lotte Information Communication, Accenture, IBM Consulting, TCS annual reports.
- **V10 residual decomposition** (15 KRW bn) — source K-IFRS Statement of Changes in Equity.
- **Cost of capital sensitivity analysis** — at 8.0% / 9.0% / 10.0%. The EVA finding's direction depends materially on the 9.0% assumption.
- **Optional Claude for Financial Services experiment** — install `financial-analysis:audit-xls` and run against Stage 3 workbook. Add `docs/decisions/2026-07-03-nguyen-ai-tooling-experiment.md` memo. Portfolio-shaping rather than rubric-required.
