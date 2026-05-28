# Stage 4 — Instructor Review

**Student:** Nguyen Anh
**Company:** Samsung SDS Co., Ltd. (018260 KS, Korea Exchange)
**Spec:** `docs/specs/2026-05-26-nguyen-samsung-sds-spec.md`
**Reviewed:** 2026-05-27

---

## Observations

### Part A — Model Specification

- **Scope & Objective (Section 1):** Clearly identifies Samsung SDS by ticker, exchange, industry, and fiscal periods. The analytical objective — evaluating operating performance across six ratio categories — is stated directly. Reporting standard (K-IFRS) and currency (KRW billion) are specified upfront, which is good practice. The section also names three benchmarking competitors (LG CNS, Accenture, Infosys) and external data sources (Damodaran, Bloomberg, KIS Value), which shows awareness that ratios in isolation need context. One area to strengthen: the objective reads more like a general description than a testable hypothesis. Connecting back to the three hypotheses from the Stage 2 memo (margin expansion from cloud mix, differential asset turnover between segments, strong liquidity from the cash-heavy balance sheet) would sharpen the analytical lens.

- **Model Architecture (Section 2):** The seven-tab workbook layout (Cover, Balance Sheet, Income Statement, Cash Flow, Ratios, Validation, Analysis) follows the recommended separation of inputs, calculations, and outputs. Color conventions are documented (blue = input, black = formula, green = output, red = exception), which is exactly what a model user needs. The rules section correctly mandates named ranges and no hardcoded formulas. This section is well structured.

- **Data Inputs (Section 3):** Balance sheet inputs are presented in a clean table with named ranges and both FY2025 and FY2024 values populated. This is strong — many students leave FY2024 columns blank. The income statement and cash flow sections, however, only show FY2025 values. For a two-year trend analysis (which the spec itself calls for in Section 8), FY2024 income statement and cash flow figures are essential. The prompt log notes that some FY2024 IS values were removed because they "were inferred rather than directly sourced from workbook data." That is a defensible decision — it is better to omit values than fabricate them — but the spec should explicitly flag this gap and state the plan for sourcing FY2024 IS/CF data before Stage 5 execution. Market inputs include market cap, share price, and shares outstanding, which is good. The assumed cost of capital (9.00%) and tax rate (27.25%) are documented as assumptions rather than as sourced data, which is the correct treatment.

- **Derived Inputs (Sections 4–5):** Section 4 establishes the naming convention (`BAL_metric_year`, `INC_metric_year`, etc.) with mandatory year suffixes, which is exactly right. Section 5 shows five derived calculations: total debt (from debt due for repayment + long-term debt), average assets, average equity, average receivables, and NOPAT. Each includes the formula in named-range notation and the numeric result. The total debt derivation is particularly noteworthy — the HIL note explains that total debt was originally treated as a raw input and was reclassified as derived after manual verification against Samsung SDS filings. That is a meaningful catch. One gap: average inventory and average accounts payable are not computed here, even though the ratio definitions in Section 6 use single-year denominators for inventory and AP turnover. If the spec intends to use averages for receivables but point-in-time for inventory and AP, that should be stated as a deliberate choice (it is defensible for Samsung SDS given the very small inventory balance of KRW 15B, but it should be explicit).

### Part A — Ratios & Validation

- **Ratio Definitions (Section 6):** The spec defines ratios across six categories: Profitability (6 ratios), Efficiency (8 ratios including CCC), Liquidity (4 ratios), Leverage (5 ratios), Market (4 ratios), and Du Pont (4 components). The total count exceeds 30, which is comprehensive and meets the rubric threshold. All formulas use named-range notation, which is correct. However, the ratios are presented as plain-text formula lines rather than in a structured table with columns for ratio name, formula, expected range, and interpretation. Tabulating them — even a simple three-column table (Ratio | Formula | Expected Direction) — would make Section 6 substantially more useful as a build reference. As written, a Stage 5 LLM or human builder would need to parse free-text blocks to extract the formula logic, which increases the risk of misinterpretation. The automated scan flagged this as "approximately 0 tabulated rows with formulas" because the formulas are embedded in prose/code blocks rather than table rows. The ratios themselves are correctly defined; the issue is presentation format, not mathematical content.

- **Validation Rules (Section 7):** Five validation rules are specified: (1) balance sheet identity with a 1% tolerance, (2) Du Pont ROE vs. direct ROE with a 0.5% tolerance, (3) no zero denominators, (4) current asset component additivity, and (5) free cash flow identity. This is a meaningful set — particularly the Du Pont cross-check and the balance sheet identity, which are the two most important integrity tests. To strengthen this section further, consider adding: (a) a retained earnings roll-forward check (beginning equity + net income - dividends should approximate ending equity), (b) a sign-consistency check (e.g., if EBIT is positive, operating margin must be positive), and (c) expected-range bounds for key ratios (e.g., current ratio should be > 0, debt-to-equity should be >= 0). These are low-effort additions that significantly improve model auditability.

### Part B — Analysis Specification

- **Analysis Requirements (Section 8):** The section identifies four analytical dimensions (profitability, efficiency, liquidity, leverage) and specifies that each should include trend analysis, driver identification, and competitor/industry benchmarking. It also calls for cross-category relationships, which is good — that is where the most interesting insights typically emerge (e.g., the relationship between Samsung SDS's massive cash position and its low leverage ratios). The section is, however, fairly brief. Adding one or two specific analytical questions per category would sharpen the guidance. For example, under Profitability: "Has the shift toward higher-margin cloud services measurably improved gross margin, or is the logistics segment diluting the effect?" Under Liquidity: "Is Samsung SDS's cash position (KRW 6.4T vs. KRW 2.3T current liabilities) creating shareholder value or representing an inefficient capital allocation?"

- **Du Pont Decomposition (Section 9):** Lists the three standard Du Pont components (profit margin, asset turnover, equity multiplier) and asks for identification of primary ROE drivers, sustainability, and strategic implications. This is adequate but could go deeper. Since Samsung SDS has an unusual profile — moderate margins, moderate asset turnover, but a very low equity multiplier due to minimal leverage — the decomposition should explicitly call out what this means: the company is generating its ROE almost entirely from operations rather than financial leverage, which is strategically conservative but may signal an under-leveraged balance sheet.

- **Strategic Recommendations (Section 10):** Requires 3-5 recommendations, each with ratio evidence, operational implication, management action, expected impact, and implementation rationale. This is a well-structured framework. The requirement that recommendations be "measurable and actionable" is exactly right.

- **Output Format (Section 11):** Specifies a nine-section report structure and a 2,500-3,500 word target with an executive management briefing tone. This gives Stage 5 enough structure to produce a coherent deliverable. Consider adding guidance on whether tables, charts, or appendices are expected within the final output.

### Prompt Log & HIL Iteration

- **Prompt log:** Documents six sessions, all using ChatGPT, on a single day (2026-05-26). The log follows the required table format with columns for inputs, purpose, prompt summary, output, and human review. The progression is logical: initial draft generation, data validation, source verification, derived-input correction, ratio expansion, and formatting cleanup. Each row clearly distinguishes what the LLM produced from what the student reviewed and changed.

- **HIL iteration:** Two strong human-in-the-loop signals stand out. First, the student identified that the initial LLM output mixed generic named ranges (e.g., `BAL_assets_total`) with year-specific ranges (e.g., `BAL_assets_total_2025`), recognized the downstream risk for Stage 5 execution, and mandated consistent year-suffix conventions across the entire spec. Second, the student caught that `BAL_total_debt` was presented as a raw financial input when it does not exist as a standalone line item in Samsung SDS's K-IFRS statements, and reclassified it as a derived input with an explicit formula. Both of these are substantive, judgment-driven corrections — not cosmetic edits — and they demonstrate exactly the kind of critical review that Stage 4 is designed to develop.

---

## Kindly-worded suggestions for improvement

- The specification demonstrates strong fundamentals: clean YAML metadata, consistent named-range conventions, comprehensive ratio coverage across all six categories, and — most importantly — genuine human-in-the-loop iteration that caught real issues in the LLM output. The debt reclassification and naming-convention standardization are exactly the kinds of interventions that separate a student who is passively accepting AI output from one who is actively auditing it.

- The primary area for improvement is **density and tabulation**. At approximately 1,000 words of prose (excluding tables and formulas), the spec is thinner than it could be. The ratio definitions in Section 6 are mathematically correct but presented as free-text formula blocks rather than structured tables. Converting them into a table format with columns for Ratio Name, Named-Range Formula, and Expected Direction/Range would make the spec substantially more useful as a build reference and would satisfy the rubric's tabulation expectation.

- The second area is **FY2024 completeness**. The balance sheet has both years populated, which is excellent, but the income statement and cash flow sections show only FY2025. Since the analysis spec (Section 8) calls for FY2024-to-FY2025 trend analysis, the prior-year IS/CF values are necessary. If the workbook does not yet contain FY2024 IS/CF data, the spec should explicitly flag this as a gap to resolve before Stage 5.

**Concrete improvements for the revision sweep:**

1. **Tabulate Section 6 ratios.** Convert the ratio definitions from plain-text formula blocks into a structured table. A three-column format works well: `| Ratio Name | Formula (Named Ranges) | Expected Range or Direction |`. This is not asking for new ratios — the formulas are already correct — it is asking for a presentation format that a builder (human or LLM) can parse unambiguously.

2. **Add FY2024 income statement and cash flow values to Section 3.** If the values are available in the workbook, populate them. If they are not yet sourced, add a row or note reading "FY2024 values: to be populated from [source]" so Stage 5 knows this is an open item rather than an intentional omission.

3. **Expand validation rules with expected-range assertions.** The five existing rules are meaningful (especially the Du Pont cross-check). Consider adding two or three more: (a) a retained earnings roll-forward (beginning equity + net income - dividends should approximate ending equity, tolerance +/- 2%), (b) sign-consistency checks (positive EBIT should produce positive operating margin), and (c) boundary checks for ratios that should never be negative (current ratio, debt-to-equity for a company with positive equity).

4. **Add one specific analytical question per category in Section 8.** For example: "Profitability — Is cloud-driven margin expansion visible in the gross margin trend, or is logistics revenue diluting the effect?" This gives Stage 5 a concrete thread to follow rather than a generic directive.

5. **Clarify the average vs. point-in-time convention for turnover denominators.** Section 5 computes average receivables but Section 6 uses point-in-time inventory and AP. Either compute averages for all three or add a note explaining why the treatment differs (e.g., inventory is immaterial at KRW 15B, so averaging adds noise rather than precision).

**Looking ahead to Stage 5**

- Samsung SDS presents an interesting analytical challenge because its financial profile is *unusual* for an IT services company: extremely high liquidity (current ratio well above 3x), minimal leverage, and moderate but stable margins. The Stage 5 analysis should lean into what makes this company distinctive rather than treating the ratios generically. The Du Pont decomposition is especially telling — ROE is driven almost entirely by operations, not leverage — and the strategic recommendations should address whether this conservative capital structure is creating or destroying shareholder value.

- When sourcing FY2024 income statement data for the trend analysis, the Samsung SDS annual report and DART filings should provide the necessary figures. If any line items require K-IFRS-to-US-GAAP adjustments for comparability with benchmarks (Accenture and Infosys report under US GAAP and IFRS respectively), note the adjustment rather than force a conversion — the goal is analytical transparency, not artificial uniformity.

- The prompt log's six-session workflow on a single day suggests concentrated effort. For Stage 5, consider spreading the work across at least two sessions with a review gap in between. Fresh eyes often catch issues that a continuous session misses, and the spec's own HIL note demonstrates that the most valuable corrections came from stepping back and re-reading critically.
