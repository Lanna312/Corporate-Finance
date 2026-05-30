# Corporate Finance Portfolio

**BUS-629 International Corporate Finance — Samsung SDS Co., Ltd. (KRX: 018260) Ratios Analysis Project**

A spec-driven, LLM-augmented, human-in-the-loop financial ratio analysis of Samsung SDS Co., Ltd. for fiscal year FY2025. Built across five stages following the workflow taught by Adam Stauffer at the Shidler College of Business (University of Hawaii) Vietnam Executive MBA (VEMBA) program.

**Author:** Nguyen Lan Anh · Director of International Business, CMC Telecom · BUS-629 VEMBA Cohort
**Course:** BUS-629 International Corporate Finance
**Faculty:** Adam Stauffer, Shidler College of Business
**LinkedIn:** [linkedin.com/in/lanna-nguyen-05545b7b](https://linkedin.com/in/lanna-nguyen-05545b7b)

---

## What You'll Find Here

This repository is a **portfolio artifact**, not a coursework dump. It documents the full process behind a multi-stage financial analysis — from initial template architecture through technical specification design, LLM-executed analysis with manual verification, and human-in-the-loop iteration. The structure follows how financial analysis is built in practice in corporate finance teams: separating templates, populated models, decision memos, technical specifications, validation work, and final deliverables into purpose-specific directories.

Three things distinguish this portfolio from a typical course submission:

1. **Spec-driven design discipline.** A formal technical specification (the v2.2 document at `docs/specs/`) defines the analytical work precisely enough that an LLM with no prior context can reproduce it. The specification is the central artifact — not the analysis itself.
2. **Human-in-the-loop (HIL) iteration is documented end-to-end.** Six iterations across two rounds are recorded in an annotated diff file, with each gap traced to a specific symptom in the LLM output and a specific spec-language fix.
3. **Executive interpretation layered on cold-context LLM output.** The Stage 5 final analysis applies four substantive domain corrections to the LLM output, grounded in Samsung SDS strategic and operating context (intra-Samsung-Group revenue structure, Vietnam regional positioning through CMC Corporation, Global Delivery Center network). The corrections are individually logged in the final analysis §5 LLM Evaluation.

The work is academic; the artifacts are professional-grade.

---

## Samsung SDS at a Glance

Samsung SDS Co., Ltd. is the ICT services subsidiary of the Samsung Group, listed on the Korea Exchange under ticker `018260.KS`. Approximately 80% of revenue is generated from intra-group Samsung affiliate work (Samsung Electronics, Samsung Display, Samsung Heavy Industries, Samsung Biologics, Samsung Engineering, and other group operating affiliates); approximately 20% from external customers. The firm operates four principal business areas — **Data Center** services, **Cloud** services, **IT Outsourcing (ITO)**, and **Digital Transformation (DX)** — plus a Logistics technology segment. Operations span Korea, Vietnam, India, China, and other regional Global Delivery Centers.

**Why this company.** Samsung SDS was selected for the BUS-629 analysis based on three criteria: (i) it satisfies all course eligibility requirements (publicly listed, non-financial, audited multi-year disclosures); (ii) it offers analytical richness across distinct operating segments and a financially conservative balance sheet; and (iii) it has direct professional relevance to the author — Samsung SDS became a strategic shareholder of CMC Corporation (parent of CMC Telecom, the author's employer) in 2019 and remains the largest shareholder. The Stage 2 selection memo at `docs/decisions/2026-05-18-nguyen-samsung-sds-selection.md` details the full selection rationale and includes the author's professional-context disclosure.

---

## Project Status

| Stage | Status | Key artifact | Reference commit |
|---|:---:|---|---|
| **Stage 0** — Repository setup | ✓ | `README.md`, `LICENSE`, `.gitignore` | `ac06372` |
| **Stage 1** — Template architecture | ✓ | [`models/templates/performance-ratios-template.xlsx`](models/templates/performance-ratios-template.xlsx) | `e37d2aa` |
| **Stage 2** — Company selection memo | ✓ (revised per instructor PR) | [`docs/decisions/2026-05-18-nguyen-samsung-sds-selection.md`](docs/decisions/2026-05-18-nguyen-samsung-sds-selection.md) | `c7a96a4` + `76aae7c` |
| **Stage 3** — Model population & validation | ✓ | [`models/builds/2026-05-21-nguyen-samsung-sds-financials.xlsx`](models/builds/2026-05-21-nguyen-samsung-sds-financials.xlsx) | `d018657` |
| **Stage 4** — Technical specification (v2.2) | ✓ (twice instructor-reviewed, +19 sweep bump toward 100) | [`docs/specs/2026-05-27-nguyen-samsung-sds-spec.md`](docs/specs/2026-05-27-nguyen-samsung-sds-spec.md) | `78f574d` |
| **Stage 5** — LLM analysis, evaluation, retrospective, polish | ✓ | [`deliverables/2026-05-28-nguyen-samsung-sds-final-analysis.md`](deliverables/2026-05-28-nguyen-samsung-sds-final-analysis.md) | *current* |

**Instructor reviews on Stage 4** (open PRs visible under the [Pull Requests tab](../../pulls)):
- PR #1 (`stage4-review-2026-05-27`) — original review of pre-rebuild v1.0 spec
- PR #2 (`stage4-sweep-2026-05-28`) — post-deadline sweep review of v2.1 rebuild, awarding +19 sweep bump with explicit "ceiling room for further iteration toward 100" guidance addressed in v2.2

---

## Key Findings (Stage 5 Final Analysis)

The full analysis lives in `deliverables/2026-05-28-nguyen-samsung-sds-final-analysis.md`. The executive-level findings:

**Operating profile.** Samsung SDS produced **KRW 783 bn net income on KRW 13,930 bn revenue** in FY2025 — a 5.6% net margin, 6.9% EBIT margin, 7.8% return on average equity. All three hypotheses from the Stage 2 selection memo are confirmed:

- **H1 — Profitability:** EBIT margin expanded ~28 bps YoY into the 6.8–7.2% expected band, driven by Cloud and Digital Transformation mix shift.
- **H2 — Efficiency:** TBD pending K-IFRS Segment Disclosure review; documented as a Stage 5 follow-up.
- **H3 — Liquidity:** Current ratio of 4.03x exceeds the 4.0x upper threshold; structural cash-richness confirmed.

**The flagged finding.** Economic Value Added is **−14 KRW bn**. After-tax operating income of KRW 924 bn falls 14 KRW bn short of the firm's 9.0% cost of capital on its KRW 10,422 bn start-of-year invested capital base. Standalone returns are *at* — not *above* — the cost-of-capital hurdle.

**The strategic reframe.** Standalone EVA understates Samsung Group consolidated value capture (cost savings, integration efficiency, IP retention on the affiliate side). The negative finding is a *capital-allocation* outcome, not an *operating-performance* outcome. The fastest path to standalone value creation runs through capital-structure reform — not margin improvement.

**Strategic recommendations** (full detail in §4 of the final analysis):

1. **Capital-structure reform** — KRW 1,000 bn tactical buyback over 24 months, coordinated with Samsung Group treasury, to lift `RATIO_leverage` from 1.31x toward 1.55x and turn EVA positive.
2. **Vietnam / SE-Asia platform scale-up** — KRW 1,500–2,000 bn over 36 months to deepen the existing CMC Corporation majority stake and expand the Global Delivery Center network (Vietnam + India + China) for ITO cost-of-delivery optimization.
3. **Working capital efficiency** — Compress `RATIO_average_collection_period` from 66.4 days to 62 days within 12 months, focused on the ~20% external customer book (the ~80% intra-Samsung-Group portion is structurally fixed by group quarterly netting).
4. **Investor communication** — Anchor FY2026–FY2027 messaging on value-creation discipline, external-customer-mix progress, and the regional platform thesis.

---

## Repository Structure

```
Corporate-Finance/
├── README.md          ← you are here
├── RESUME.md          ← professional resume
├── BIO.md             ← extended professional biography
├── LICENSE            ← MIT
├── .gitignore
│
├── docs/              ← written documentation, decisions, specifications
│   ├── decisions/     ← Stage 2 company selection memo + instructor PR feedback responses
│   ├── feedback/      ← instructor review files (when merged from PR branches)
│   └── specs/         ← Stage 4 technical specification (v2.2)
│
├── models/            ← financial models and spreadsheet builds
│   ├── templates/     ← Stage 1 ratios template
│   └── builds/        ← Stage 3 populated Samsung SDS financial workbook
│
├── data/              ← source financial data and provenance documentation
│                        (FY2024 and FY2025 Samsung SDS audited financials)
│
├── analysis/          ← validation work and HIL iteration artifacts
│   └── validation/    ← Stage 4 annotated diff, Stage 5 manual ratio verification
│
└── deliverables/      ← final presentation-ready outputs
                         (Stage 5 raw LLM output, evaluated final analysis,
                          spec retrospective, full prompt log)
```

### Directory Overview

| Directory | Purpose |
|---|---|
| **docs/** | Written documentation, project decisions, technical specifications, instructor feedback |
| **models/** | Financial models, ratio templates, populated spreadsheet builds |
| **data/** | Source financial data (audited filings) and provenance documentation |
| **analysis/** | Validation work, sensitivity analysis, HIL iteration evidence |
| **deliverables/** | Final presentation-ready outputs and the cross-stage prompt log |

---

## How to Navigate the Repository

If you are a manager, reviewer, or peer who just clicked the repo link, the recommended reading order is:

1. **Start here:** the **Stage 5 evaluated final analysis** at [`deliverables/2026-05-28-nguyen-samsung-sds-final-analysis.md`](deliverables/2026-05-28-nguyen-samsung-sds-final-analysis.md). It is the executive deliverable — analysis, four strategic recommendations, executive justification in author voice.
2. **For the spec-driven methodology:** read the **Stage 4 technical specification (v2.2)** at [`docs/specs/2026-05-27-nguyen-samsung-sds-spec.md`](docs/specs/2026-05-27-nguyen-samsung-sds-spec.md). This document defines every ratio, every named range, and every analytical instruction precisely enough that a cold-context LLM can reproduce the analysis.
3. **For the LLM-evaluation discipline:** read the **Stage 5 spec retrospective** at [`deliverables/2026-05-28-nguyen-samsung-sds-spec-retrospective.md`](deliverables/2026-05-28-nguyen-samsung-sds-spec-retrospective.md) and the **manual verification table** at [`analysis/validation/2026-05-28-nguyen-samsung-sds-stage5-verification.md`](analysis/validation/2026-05-28-nguyen-samsung-sds-stage5-verification.md). Together they document what the spec specified well, what it missed, and how author judgment refined the LLM output.
4. **For the HIL iteration record:** read the **Stage 4 annotated diff** at [`analysis/validation/2026-05-27-nguyen-samsung-sds-stage4-iteration.md`](analysis/validation/2026-05-27-nguyen-samsung-sds-stage4-iteration.md) and the **full prompt log** at [`deliverables/prompt-log.md`](deliverables/prompt-log.md). They document twelve LLM sessions, six iterations across two rounds, and the cross-round HIL discipline.
5. **For the source data:** the **Stage 3 populated workbook** at [`models/builds/2026-05-21-nguyen-samsung-sds-financials.xlsx`](models/builds/2026-05-21-nguyen-samsung-sds-financials.xlsx) contains the underlying Samsung SDS FY2024 and FY2025 financial data with all twenty-seven ratios computed.

---

## Methodology Highlights

**Spec-driven design.** The Stage 4 technical specification (v2.2) is the central artifact — defining model architecture, data inputs, named-range conventions, derived inputs, twenty-seven ratios across six categories, fourteen validation rules, six per-category anchoring questions, and a five-field hypothesis-evaluation framework. The spec went through three rounds of revision (v1.0 → v2.0 → v2.1 → v2.2) and received two instructor PR reviews. The v2.2 closes both the original review gaps and the sweep-review ceiling-room recommendations.

**Cold-context LLM execution.** Stage 5 deliberately feeds *only* the spec v2.2 to Claude Opus 4.7 — no prior context, no Stage 3 workbook attachment, no conversational history. This tests whether the spec stands alone and produces the empirical evidence for the spec retrospective. The raw LLM output is preserved unedited at `deliverables/2026-05-28-nguyen-samsung-sds-llm-raw.md`.

**Manual ratio verification.** Seven ratios across all six spec categories were recomputed by hand from the Stage 3 workbook values and compared to LLM-stated values. The verification deliberately targets ratio types most prone to LLM error: averaging conventions, day-count conventions (365 vs 360), multi-component reconciliation, formula composition variants. All seven match within rounding tolerance — itself a meaningful finding about spec specificity.

**Human-in-the-loop iteration.** Six substantive iterations are documented in the Stage 4 annotated diff and four domain corrections are logged in the Stage 5 final analysis. Each iteration and each correction traces the gap to a specific symptom and the specific spec language or domain context that addressed it.

**Author professional-context disclosure.** The author is Director of International Business at CMC Telecom and has direct professional exposure to the Samsung SDS–CMC Corporation ecosystem since 2019 (Samsung SDS is the largest shareholder of CMC Corporation). All financial figures in the analysis come from public K-IFRS filings only; no non-public information from the CMC Telecom role is used in the financial analysis. The disclosure is documented in §1.5 of the Stage 5 final analysis.

---

## Workflow

Project work generally follows the process below:

1. **Define objectives and assumptions.** Stage 2 selection memo and Stage 4 specification §1 Scope & Objective.
2. **Gather supporting documentation and data.** Source data in `data/`; Stage 3 model population in `models/builds/`.
3. **Build financial models.** Stage 1 template and Stage 3 populated workbook.
4. **Specify the analytical work.** Stage 4 technical specification.
5. **Validate calculations and outputs.** Stage 4 fourteen validation rules; Stage 5 manual ratio verification.
6. **Execute, evaluate, and refine.** Stage 5 LLM raw output, evaluated final analysis with author domain corrections, spec retrospective closing the feedback loop.
7. **Polish for portfolio presentation.** This README, per-directory READMEs, consistent filename convention, clean commit history.

The full prompt log at `deliverables/prompt-log.md` records all twelve LLM sessions used across Stages 4 and 5 with input lists, prompt intents, output summaries, and human review actions.

---

## Portfolio Information

Additional professional materials at the repository root:

- **[BIO.md](BIO.md)** — extended professional biography
- **[RESUME.md](RESUME.md)** — professional resume
- **LinkedIn:** [linkedin.com/in/lanna-nguyen-05545b7b](https://linkedin.com/in/lanna-nguyen-05545b7b)

---

## License

This portfolio is released under the **MIT License** (see [LICENSE](LICENSE)). All financial figures and analysis come from publicly disclosed K-IFRS filings and other public sources. No non-public information is used. The author's professional-context disclosure is provided in §1.5 of the Stage 5 final analysis.

---

## Contact

For questions about the methodology, the analysis, or the portfolio approach:

**Nguyen Lan Anh** · Director of International Business, CMC Telecom · BUS-629 VEMBA Cohort
LinkedIn: [linkedin.com/in/lanna-nguyen-05545b7b](https://linkedin.com/in/lanna-nguyen-05545b7b)

---

*Repository contents are stable as of the Stage 5 deliverable date (2026-05-28). Post-deadline polish updates may be applied per the course's revision-sweep policy without invalidating the stage-locked scoring.*
