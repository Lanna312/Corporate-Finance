# Prompt Log

| Date | Stage | Tool | Inputs / Files Provided | Purpose | Key Prompt Summary | Output / Result | Human Review & Changes |
|---|---|---|---|---|---|---|---|
| 2026-05-26 | Stage 4 | ChatGPT | Stage 4 brief URL; spec-template URL; performance-ratios-template.xlsx; Samsung SDS financial workbook | Initial specification generation | Requested a complete Samsung SDS technical specification using the Stage 4 template structure. Required all Part A items (1–7) and Part B items (8–11), YAML frontmatter retention, named-range notation, and assumptions collection before drafting. | Generated initial technical specification draft including model architecture, ratio sections, and preliminary financial inputs. | Reviewed output and identified inconsistencies in named ranges, missing metadata fields, and unsupported financial assumptions. |
| 2026-05-26 | Stage 4 | ChatGPT | Existing Stage 4 draft + Samsung SDS workbook | Data validation and revision | Requested replacement of placeholders with workbook values, addition of ticker/exchange/version metadata, and standardization of named ranges using mandatory year suffix conventions (_2025, _2024). | Added YAML metadata fields (`018260 KS`, `Korea Exchange`, version 2.0), revised formulas, and populated additional workbook values. | Identified that several values still lacked direct workbook sourcing and some formulas used mixed naming conventions. |
| 2026-05-26 | Stage 4 | ChatGPT | Existing Stage 4 draft + workbook verification comments | Financial source verification | Requested verification of debt sourcing and validation against Samsung SDS financial statements. | Initially produced BAL_total_debt values without documenting source logic. | Determined that Total Debt did not exist as a direct financial statement line item and required reconstruction from debt due for repayment plus long-term debt. |
| 2026-05-26 | Stage 4 | ChatGPT | Existing draft + workbook review | Derived-input correction | Requested debt restructuring and explicit formula documentation. | Reclassified debt into Derived Inputs and documented formulas: debt due for repayment + long-term debt. | Confirmed consistency with workbook and prevented unsupported assumptions from appearing as raw financial inputs. |
| 2026-05-26 | Stage 4 | ChatGPT | Existing draft + workbook | Ratio model expansion | Requested expansion of ratio inventory to satisfy Stage 4 rubric requiring complete ratio definitions and validation. | Expanded specification from approximately 12–13 ratios to >30 ratios covering profitability, efficiency, liquidity, leverage, market, and DuPont categories. | Verified formulas used named-range notation only and aligned ratios with workbook structure. |
| 2026-05-26 | Stage 4 | ChatGPT | Existing draft + GitHub preview review | Markdown and rendering cleanup | Requested formatting improvements after reviewing GitHub rendering behavior. | Simplified equations, standardized markdown tables, and improved readability. | Added specification completeness check and reformatted formula presentation for cleaner GitHub rendering. |

---

## Before/After HIL Iteration Note

The most consequential issue identified in the initial LLM-generated draft involved inconsistent variable naming conventions and unsupported assumptions within the financial model structure. The first version mixed generic variables such as `BAL_assets_total` with year-specific variables such as `BAL_assets_total_2025`. This ambiguity created a major downstream risk because Stage 5 relies entirely on the specification as a standalone document. Without explicit year conventions, a later LLM could incorrectly determine whether calculations should use FY2025 values, FY2024 values, or average balances. This would likely create denominator inconsistencies and incorrect ratio outputs, particularly within ROA, ROE, and DuPont calculations.

Additional review identified a second major issue involving unsupported financial assumptions. The initial specification included `BAL_total_debt_2025` as though it existed directly in Samsung SDS financial statements. Manual workbook verification showed that Total Debt was not a reported line item. Instead, it had to be reconstructed using debt due for repayment plus long-term debt. FY2024 income statement values were also removed because they were inferred rather than sourced directly from workbook data.

The specification was revised so all financial variables follow mandatory `_2025` and `_2024` suffix conventions, formulas were updated accordingly, debt was reclassified as a derived input, metadata fields (`ticker`, `exchange_name`, `version 2.0`) were added, and ratio coverage expanded to more than 30 ratios. These changes improved reproducibility, reduced ambiguity, and strengthened Stage 5 execution reliability.

---

## Final Quality Review

Final specification checklist:

✓ Part A items 1–7 completed  
✓ Part B items 8–11 completed  
✓ YAML metadata completed  
✓ numerical values populated from workbook  
✓ year suffix conventions standardized  
✓ formulas converted to named-range notation  
✓ ratio inventory expanded to >25 ratios  
✓ validation rules included  
✓ HIL evidence included  
✓ GitHub markdown formatting reviewed
