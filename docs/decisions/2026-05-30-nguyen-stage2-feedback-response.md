---
template: stage2-feedback-response
purpose: "Documented response to instructor PR feedback on Stage 2 company selection memo, demonstrating feedback incorporation per Stage 5 rubric criterion (5% of Stage 5 score)"
author: Nguyen Lan Anh
date: 2026-05-30
company: "Samsung SDS Co., Ltd. (KRX: 018260)"
courses: [BUS-629]
stage: 5
references:
  - "docs/decisions/2026-05-18-nguyen-samsung-sds-selection.md (original Stage 2 memo)"
  - "Commit 76aae7c (Stage 2 memo revision in response to instructor feedback)"
  - "docs/feedback/stage5-review-2026-05-30.md (Stage 5 review noting this gap)"
---

# Stage 2 Feedback Response Memo

**To:** Adam Stauffer · Faculty, BUS-629 International Corporate Finance · Shidler College of Business
**From:** Nguyen Lan Anh · Director of International Business, CMC Telecom · VEMBA Cohort
**Date:** 2026-05-30
**Re:** Documented response to Stage 2 PR feedback on the Samsung SDS company selection memo

---

## Executive Summary

This memo documents the changes I made to the Stage 2 company selection memo (`docs/decisions/2026-05-18-nguyen-samsung-sds-selection.md`) in response to the instructor's PR review feedback received between Stage 2 and Stage 4. The revisions were committed under commit `76aae7c` ("Update Memo for Company Selection — Revise Memo following professor comments of length of memo and affirmation of hypothesis framing"). This follow-up memo makes the feedback response visible per the Stage 5 rubric criterion on Stage 2 feedback incorporation (5% of Stage 5 score) and addresses the instructor's note in the Stage 5 review (`docs/feedback/stage5-review-2026-05-30.md`) that the response was not detected.

---

## §1 Background

The original Stage 2 memo was submitted on 2026-05-18 and underwent instructor review prior to the Stage 4 specification work. The instructor PR comments on the Stage 2 memo were addressed in commit `76aae7c` on 2026-05-22 — before the start of Stage 3 model population. The revised memo lives at `docs/decisions/2026-05-18-nguyen-samsung-sds-selection.md` (final state on `main` branch).

The Stage 5 instructor review (PR #3, 2026-05-30) noted that the response was not visible to the rubric parser because (a) the original PR review was provided as conversational feedback rather than as a tracked PR review, and (b) the commit message references "professor comments" in general terms rather than specific PR comment numbers. This follow-up memo closes both gaps by documenting the feedback categories and the specific revisions made in response.

---

## §2 Categories of feedback received and corresponding revisions

### §2.1 Memo length and structural discipline

**Feedback (paraphrased):** The original memo was longer than the brief's executive-memo target and contained sections that drifted into detail more appropriate for a Stage 5 analytical deliverable than for a Stage 2 selection rationale.

**Revisions made in commit `76aae7c`:**

1. **Tightened the Executive Summary** to a single paragraph stating the company recommendation, the K-IFRS reporting basis, and the three principal selection criteria (analytical eligibility, business profile, professional relevance) — without preempting the Stage 5 analytical conclusions.
2. **Consolidated the "Background — Selection Rationale — Data Availability" sections** into a single Method section with three subsections, eliminating duplication between the Background context and the Selection Rationale paragraphs.
3. **Reduced the "Preliminary Observations" hypothesis section** from open-ended analytical commentary to three crisp hypothesis statements (H1 Profitability, H2 Efficiency, H3 Liquidity), each with a quantitative threshold testable at Stage 5 — instead of analytical narrative that would have prejudged the Stage 5 work.
4. **Moved the Two-Year Financial Snapshot table** into a tighter format with year-over-year delta column instead of separate prose paragraphs per metric.

**Net effect:** Memo length compressed; structural discipline now matches the executive-memo format the brief targets.

### §2.2 Hypothesis framing and affirmation discipline

**Feedback (paraphrased):** The original memo stated hypotheses but treated them as nearly-foregone conclusions rather than as testable propositions to be empirically affirmed or refuted at Stage 5. The hypothesis affirmation framing was too soft.

**Revisions made in commit `76aae7c`:**

1. **Restructured each of the three hypotheses (H1, H2, H3)** to follow a uniform format: (a) directional claim, (b) quantitative threshold, (c) rationale based on FY2024 observed values, (d) explicit "directly testable in Stage 3" affirmation that the hypothesis is empirical rather than asserted. This format anticipates the Stage 4 hypothesis-evaluation framework that became §8.2 of the spec v2.2 (five-field framework with Strategic Implication row).
2. **Removed prejudgment language** — the original memo had phrases like "Samsung SDS should show" and "we will see" that overcommitted the analytical conclusion before Stage 5 had been run. The revised memo uses "I expect" and "is directly testable" — preserving the analytical openness to refutation.
3. **Added explicit threshold language** to each hypothesis (e.g., H1's "6.8–7.2% expected band"; H3's "above approximately 3.8x–4.0x"). The thresholds carried forward into the Stage 4 spec v2.2 §8.2 framework and into the Stage 5 final analysis H1/H2/H3 tests, where they served as the empirical pass/fail criterion. H1 and H3 confirmed within their stated thresholds; H2 deferred pending K-IFRS Segment Disclosure access.

**Net effect:** Hypotheses framed as testable propositions with explicit thresholds, not as soft predictions. The discipline carried through Stage 4 spec design and Stage 5 analytical execution.

### §2.3 Professional context disclosure

**Feedback (paraphrased):** The original memo mentioned the author's professional context (Director of International Business at CMC Telecom; Samsung SDS strategic stake in CMC Corporation since 2019) but did not formalize the conflict-of-interest discipline.

**Revisions made in commit `76aae7c`:**

1. **Added an explicit conflict-of-interest disclosure paragraph** stating that (a) Samsung SDS became a strategic shareholder of CMC Corporation in 2019; (b) the author has professional ties to the Samsung SDS–CMC ecosystem through her CMC Telecom role; (c) all financial figures in the analysis come from public K-IFRS filings only; (d) no non-public information from the CMC Telecom role is used in the financial analysis.
2. **Documented the rationale for including the professional context** despite the conflict — the relationship provides analytical richness and industry-grounded interpretation that strengthens the analysis, provided the disclosure is transparent.

**Net effect:** The professional-context disclosure pattern established at Stage 2 carried through to the Stage 5 final analysis §1.5, where the same disclosure appears verbatim.

---

## §3 Cross-references — where the Stage 2 feedback shaped subsequent stages

The Stage 2 feedback revisions shaped the analytical and structural discipline carried forward into Stages 3, 4, and 5:

| Stage | Where the Stage 2 feedback carried forward |
|---|---|
| Stage 3 (Model population) | Hypothesis thresholds (H1: 6.8–7.2% band; H3: ≥3.8x) were the targets the populated workbook had to support. The Stage 3 workbook produced the actual values that the Stage 5 hypothesis tests used. |
| Stage 4 spec v1.0 → v2.2 (Specification) | The five-field hypothesis-evaluation framework in §8.2 (Hypothesis / Operationalization / Test methodology / Result / Strategic implication) is a structural elaboration of the discipline introduced in the revised Stage 2 memo. The §6.1 flagged-finding pattern for the negative-EVA discovery uses the same "directional claim + empirical test" framing as the Stage 2 hypotheses. |
| Stage 5 final analysis (Execution) | The hypothesis tests at §2.1 (Performance), §2.2 (Profitability), §2.4 (Leverage), §2.5 (Liquidity), and §3 (Du Pont) all reference the §8.2 framework rows. The H1/H3 confirmations and the H2 disclosed-scope deferral all use the discipline carried forward from the revised Stage 2 hypotheses. The author professional-context disclosure at §1.5 of the Stage 5 final analysis carries forward verbatim from the Stage 2 conflict-of-interest paragraph. |

---

## §4 Why this response is documented as a follow-up memo

The Stage 5 review noted that the rubric parser did not detect the Stage 2 feedback response in either of the two acceptable forms (commit messages referencing specific PR comments, or a follow-up memo). Two factors contributed:

1. **The original Stage 2 PR feedback was provided as conversational review** between the instructor and the author, not as a tracked PR review with numbered comments. There were no "PR comment #1, #2, #3" references for the Stage 2 revision commit to cite.
2. **The Stage 2 revision commit message** ("Update Memo for Company Selection — Revise Memo following professor comments of length of memo and affirmation of hypothesis framing") references the categories of feedback but does not enumerate specific PR comments.

This follow-up memo is the second acceptable form. It documents the feedback categories received, the specific revisions made in response, and the cross-reference trail through Stages 3, 4, and 5. The intent is to make the feedback response visible to the rubric parser and to provide the grader with a concise audit trail.

---

## §5 Cross-references

- **Original Stage 2 memo (revised state on `main`):** `docs/decisions/2026-05-18-nguyen-samsung-sds-selection.md`
- **Stage 2 revision commit:** `76aae7c` ("Update Memo for Company Selection — Revise Memo following professor comments of length of memo and affirmation of hypothesis framing")
- **Stage 4 spec v2.2 §8.2 hypothesis-evaluation framework:** `docs/specs/2026-05-27-nguyen-samsung-sds-spec.md` §8.2 (where the Stage 2 hypothesis discipline became a formal five-field framework)
- **Stage 5 final analysis hypothesis tests:** `deliverables/2026-05-28-nguyen-samsung-sds-final-analysis.md` §2 (where the §8.2 framework was executed against the populated workbook)
- **Stage 5 instructor review noting this gap:** `docs/feedback/stage5-review-2026-05-30.md` ("Kindly-worded suggestions for improvement")
- **Author professional-context disclosure (consistent across stages):** Stage 2 memo §Method; Stage 5 final analysis §1.5

---

*This follow-up memo is submitted as part of the Stage 5 revision pass on branch `stage5-revisions-nguyen` to address the Stage 5 instructor review note on Stage 2 feedback incorporation visibility.*
