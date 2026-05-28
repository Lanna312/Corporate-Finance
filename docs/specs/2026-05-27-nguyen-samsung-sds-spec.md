---
template: spec
purpose: "Technical specification for BUS-629 ratios analysis — Samsung SDS Co., Ltd. (KRX: 018260). Defines scope, inputs, formulas, validation, and analysis requirements with sufficient precision that an LLM with no prior context can reproduce or verify the FY2025 ratio model and produce a comprehensive ratio analysis with strategic recommendations."
audience: student
fields_required: [title, author, date, version, company, scope, model_architecture, data_inputs, named_range_conventions, derived_inputs, formulas, validation, analysis_requirements, du_pont, strategic_recommendations, output_format, references]
naming_convention: "YYYY-MM-DD-{slug}.md"
courses: [BUS-629]
notes: "Samsung SDS Co., Ltd., K-IFRS reporting standard, KRW reporting currency (billions), Current fiscal year FY2025 with FY2024 as Prior. The Stage 3 workbook is a single-year analytical model: Balance Sheet uses curr/prior suffix for FY2025/FY2024; Income Statement and Cash Flow Statement contain Current-year (FY2025) data only. Named ranges in this spec match the convention built into the workbook exactly. Output audience is hybrid executive + academic."
---

# Samsung SDS Co., Ltd. (KRX: 018260) — Accounting Ratios Analysis Specification

**Author:** Nguyen Lan Anh
**Date:** 2026-05-27
**Version:** 2.1
**Company:** Samsung SDS Co., Ltd., Ticker 018260.KS, Korea Exchange (KRX)

> **Changelog**
> - **v2.1 (2026-05-27)** — Added dedicated §4 *Named Range Conventions* master map (rubric Part A item 4). Renumbered subsequent sections. Tightened §11 Output Format alignment.
> - **v2.0 (2026-05-27)** — Aligned all named ranges to the `_curr` / `_prior` convention used in the Stage 3 workbook (replacing the year-suffix convention drafted in v1.0). Corrected Du Pont decomposition from 3-component to the 4-component extended form actually built into the workbook (`RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden`). Populated every Data Input value numerically from the Stage 3 workbook. Added analytical requirement (§8) flagging the negative-EVA finding (−14 KRW bn) surfaced during population — see HIL note in the prompt log.
> - **v1.0 (2026-05-27)** — Initial LLM-drafted skeleton from spec template, Stage 4 brief, and Stage 2 memo (pre-Stage-3 data).

---

## 1. Scope & Objective

This specification defines the model and analytical work for a multi-ratio financial performance analysis of **Samsung SDS Co., Ltd.** (KRX: 018260) for fiscal year **FY2025** (year ended **December 31, 2025**), with **FY2024 used as the Prior-year balance sheet for averaging and start-of-year denominators**.

**Reporting standard:** Korean IFRS (K-IFRS), as filed with the Financial Supervisory Service (DART) and audited by Samil PricewaterhouseCoopers. Certain K-IFRS line items have been consolidated into template categories for workbook compatibility (per workbook footnote on the Balance Sheet tab).

**Reporting currency:** Korean Won (KRW), expressed in **billions** throughout the model unless otherwise noted (`KRW bn`). Share price is in KRW per share; shares outstanding are in millions.

**Analytical objective:** Quantify and interpret Samsung SDS's FY2025 profitability, efficiency, leverage, liquidity, and market-value characteristics; test the three hypotheses raised in the Stage 2 selection memo (margin expansion via cloud / digital-transformation mix, asset-light IT services driving efficiency, structurally high liquidity); surface the negative-EVA finding that the company is earning marginally below its 9.0% cost of capital; compare to Korean and global IT-services peers; and deliver four actionable strategic recommendations to senior finance leadership.

**Intended audience for Stage 5 output:** Hybrid executive + academic — Adam Stauffer (BUS-629 grader) and a CFO-level executive reviewer. The output must lead with a one-page executive summary and follow with a structured analytical body that documents methodology and ratio derivations.

---

## Part A — Model Specification

### 2. Model Architecture

The Excel workbook (`models/builds/2026-05-21-nguyen-samsung-sds-financials.xlsx`) is organized into five tabs that separate inputs, calculations, and outputs:

| Tab | Purpose | Content |
|-----|---------|---------|
| **Cover** | Document control | Title, author, version, fiscal years, currency, reporting standard, list of tabs |
| **Balance Sheet** | Two-year BS data | Assets, Liabilities & Equity for FY Current (FY2025) and FY Prior (FY2024) |
| **Income Statement** | Current-year IS | FY2025 only — Net sales through Net income, with % of Sales column |
| **Cash Flow Statement** | Current-year CFS | FY2025 only — Operations, Investments, Financing |
| **Ratios & Derived Inputs** | All derived values + 27 ratios | Inputs (share price, shares, cost of capital, tax rate); Start of Year, Current Year, and Mixed Year (Averages) derived blocks; six ratio categories with output, formula reference, and named-range labels |

**Input / calculation / output separation.** Inputs sit in the Balance Sheet, Income Statement, and Cash Flow tabs (blue, yellow-highlighted). Derived intermediates and final ratios live in the Ratios & Derived Inputs tab (black formulas, green tab-cross references). No formula in the Ratios tab references another Ratios cell except via named ranges.

**Color coding** (Wall Street financial-modeling convention):

- **Blue text (RGB 0,0,255)** — hardcoded inputs (audited financial statements, DART filings, KRX market data)
- **Black text (RGB 0,0,0)** — formulas and calculated values
- **Green text (RGB 0,128,0)** — links from other tabs within the workbook
- **Yellow background** — input cells the user can change (share price, cost of capital, tax rate)
- **Light grey background** — calculated subtotals / totals

**Formatting rules:**

- Currency: `#,##0` format, unit suffix on header (`KRW billion`)
- Percentages: `0.0%` format
- Multiples: `0.00x` format (workbook displays `1,05x` in European decimal style — equivalent to `1.05x`)
- Days values shown to one decimal (`66.4 days`)
- Negatives: parentheses `(123)`
- Years: text strings (`2024`, `2025`)
- Font: Arial 10 throughout

---

### 3. Data Inputs

All values in **KRW billions** unless otherwise noted. Source: Samsung SDS Annual Report 2025; DART K-IFRS filings; KRX market data (Dec 30, 2025 close).

**3.1 Balance Sheet — FY2024 (Prior) and FY2025 (Current)**

| Line item | FY2024 (Prior) | FY2025 (Current) |
|---|---:|---:|
| Cash and marketable securities | 6,024 | 6,380 |
| Receivables | 2,534 | 2,595 |
| Inventories | 19 | 15 |
| Other current assets | 427 | 416 |
| **Total current assets** | **9,004** | **9,406** |
| Property, plant & equipment (gross) | 3,730 | 3,924 |
| Less accumulated depreciation | 1,956 | 2,171 |
| **Net tangible fixed assets** | **1,774** | **1,753** |
| Intangible assets (goodwill) | 814 | 824 |
| Other assets | 1,647 | 1,471 |
| **Total Assets** | **13,238** | **13,454** |
| Debt due for repayment (short-term debt) | 267 | 262 |
| Accounts payable | 707 | 585 |
| Other current liabilities | 1,522 | 1,485 |
| **Total current liabilities** | **2,495** | **2,332** |
| Long-term debt | 717 | 555 |
| Other long-term liabilities | 320 | 304 |
| **Total Liabilities** | **3,533** | **3,191** |
| Common stock and paid-in capital | 1,710 | 1,733 |
| Retained earnings | 7,995 | 8,530 |
| **Total shareholders' equity** | **9,705** | **10,263** |
| **Total Liabilities + Equity** | **13,238** | **13,454** |

**3.2 Income Statement — FY2025 (Current fiscal year only)**

| Line item | FY2025 | % of Sales |
|---|---:|---:|
| Net sales | 13,930 | 100.0% |
| less Cost of goods sold | 11,510 | 82.6% |
| less Selling, general & administrative expenses | 1,031 | 7.4% |
| less Depreciation | 432 | 3.1% |
| **Earnings before interest and taxes (EBIT)** | **957** | **6.9%** |
| plus Other income | 313 | 2.2% |
| less Interest expense | 194 | 1.4% |
| **Taxable income** | **1,076** | **7.7%** |
| less Taxes | 293 | 2.1% |
| **Net income** | **783** | **5.6%** |
| Dividends | 233 | 1.7% |
| Addition to retained earnings | 550 | 3.9% |

> **Note:** The Stage 3 workbook contains FY2025 Income Statement only. FY2024 Income Statement values referenced in the Stage 2 memo (Revenue 13,828; EBIT 911; Net income 790) are used **for hypothesis context only** in §8.1, not as named ranges in the model.

**3.3 Cash Flow Statement — FY2025 (Current fiscal year only)**

| Line item | FY2025 |
|---|---:|
| **Operations** | |
| Net income | 783 |
| plus Depreciation | 432 |
| Decrease (increase) in accounts receivable | (69) |
| Decrease (increase) in inventories | 4 |
| Decrease (increase) in other current assets | 20 |
| Increase (decrease) in accounts payable | (123) |
| Increase (decrease) in other current liabilities | 15 |
| **Total change in working capital** | **(153)** |
| **Cash provided by operations** | **1,061** |
| **Investments** | |
| Capital expenditures | (386) |
| plus Sales (acquisitions) of long-term assets | 15 |
| plus Other investing activities | (478) |
| **Cash provided by (used for) investments** | **(849)** |
| **Financing** | |
| Increase (decrease) in short-term debt | — |
| plus Increase (decrease) in long-term debt | (167) |
| plus Dividends paid | (233) |
| plus Issues (repurchases) of stock | — |
| plus Other | 33 |
| **Cash provided by (used for) financing** | **(367)** |
| **Net increase (decrease) in cash** | **(154)** |

> **Note:** Per workbook footnote, the net change in cash of (154) reconciles to underlying K-IFRS Cash & Cash Equivalents change of (110), with KRW 43.8 bn attributed to FX-rate fluctuations on cash balances.

**3.4 Market Data and Assumptions — FY2025 close**

| Item | Value | Unit |
|---|---:|---|
| Share price (KRX last trading day Dec 30, 2025) | 186,500 | KRW per share |
| Shares outstanding | 77 | Million shares |
| Cost of capital (assumption) | 9.0% | % |
| Effective tax rate (assumption) | 27.3% | % |
| Market capitalization (derived) | 14,431 | KRW bn |

---

### 4. Named Range Conventions

Master map of every named range in the workbook to its value and source. Stage 5 must reference these named-range labels exactly when computing or validating ratios.

**Naming pattern in this workbook:**
- `BAL_*` — Balance Sheet items; suffix `_curr` (FY2025) or `_prior` (FY2024)
- `INC_*` — Income Statement items (FY2025 only, no suffix)
- `CFS_*` — Cash Flow Statement items (FY2025 only, no suffix)
- `startYear_*` — Prior-year balance sheet references used as start-of-year denominators
- `currentYear_*` — Current-year balances or derived current-year values
- `avg_*` — Two-period (start + current) averages
- `RATIO_*` — Final ratio outputs in the Ratios tab
- Scalar inputs (no prefix): `share_price`, `shares_outstanding`, `cost_capital`, `tax_rate`, `market_capitalization`

**4.1 Balance Sheet named ranges (KRW bn)**

| Named range | FY2024 (prior) | FY2025 (curr) |
|---|---:|---:|
| `BAL_cash_marketable_securities_*` | 6,024 | 6,380 |
| `BAL_receivables_*` | 2,534 | 2,595 |
| `BAL_inventories_*` | 19 | 15 |
| `BAL_other_current_assets_*` | 427 | 416 |
| `BAL_assets_current_*` | 9,004 | 9,406 |
| `BAL_ppe_gross_*` | 3,730 | 3,924 |
| `BAL_accumulated_depreciation_*` | 1,956 | 2,171 |
| `BAL_ppe_net_*` | 1,774 | 1,753 |
| `BAL_intangibles_*` | 814 | 824 |
| `BAL_other_assets_*` | 1,647 | 1,471 |
| `BAL_assets_total_*` | 13,238 | 13,454 |
| `BAL_debt_short_term_*` | 267 | 262 |
| `BAL_accounts_payable_*` | 707 | 585 |
| `BAL_other_current_liabilities_*` | 1,522 | 1,485 |
| `BAL_liabilities_current_*` | 2,495 | 2,332 |
| `BAL_debt_long_term_*` | 717 | 555 |
| `BAL_other_long_term_liabilities_*` | 320 | 304 |
| `BAL_liabilities_total_*` | 3,533 | 3,191 |
| `BAL_common_stock_*` | 1,710 | 1,733 |
| `BAL_retained_earnings_*` | 7,995 | 8,530 |
| `BAL_equity_shareholders_*` | 9,705 | 10,263 |

> Replace `*` with `curr` for FY2025 or `prior` for FY2024.

**4.2 Income Statement named ranges (KRW bn, FY2025)**

| Named range | Value |
|---|---:|
| `INC_sales` | 13,930 |
| `INC_cost_goods_sold` | 11,510 |
| `INC_sga` | 1,031 |
| `INC_depreciation` | 432 |
| `INC_ebit` | 957 |
| `INC_other_income` | 313 |
| `INC_interest_expense` | 194 |
| `INC_taxable_income` | 1,076 |
| `INC_taxes` | 293 |
| `INC_net` | 783 |
| `INC_dividends` | 233 |
| `INC_addition_retained_earnings` | 550 |

**4.3 Cash Flow Statement named ranges (KRW bn, FY2025)**

| Named range | Value |
|---|---:|
| `CFS_net_income` | 783 |
| `CFS_depreciation` | 432 |
| `CFS_change_receivables` | (69) |
| `CFS_change_inventories` | 4 |
| `CFS_change_other_current_assets` | 20 |
| `CFS_change_accounts_payable` | (123) |
| `CFS_change_other_current_liabilities` | 15 |
| `CFS_change_working_capital` | (153) |
| `CFS_operating` | 1,061 |
| `CFS_capex` | (386) |
| `CFS_sale_long_term_assets` | 15 |
| `CFS_other_investing` | (478) |
| `CFS_investing` | (849) |
| `CFS_change_short_term_debt` | — |
| `CFS_change_long_term_debt` | (167) |
| `CFS_dividends_paid` | (233) |
| `CFS_stock_issuance` | — |
| `CFS_other_financing` | 33 |
| `CFS_financing` | (367) |
| `CFS_net_change_cash` | (154) |

**4.4 Scalar inputs and assumptions**

| Named range | Value | Unit |
|---|---:|---|
| `share_price` | 186,500 | KRW per share |
| `shares_outstanding` | 77 | Million shares |
| `cost_capital` | 9.0% | % |
| `tax_rate` | 27.3% | % |
| `market_capitalization` | 14,431 | KRW bn |

**4.5 Derived named ranges** — formulas defined in §5; values shown for reference.

| Named range | Value |
|---|---:|
| `startYear_equity` | 9,705 |
| `startYear_inventory` | 19 |
| `startYear_receivables` | 2,534 |
| `startYear_total_assets` | 13,238 |
| `startYear_total_capitalization` | 10,422 |
| `currentYear_after_tax_operating_income` | 924 |
| `currentYear_daily_sales_average` | 38.16 |
| `currentYear_equity` | 10,263 |
| `currentYear_cash_marketable_securities` | 6,380 |
| `currentYear_assets_current` | 9,406 |
| `currentYear_liabilities_current` | 2,332 |
| `currentYear_cost_goods_sold_daily` | 31.53 |
| `currentYear_debt_long_term` | 555 |
| `currentYear_working_capital_net` | 7,074 |
| `currentYear_assets_total` | 13,454 |
| `currentYear_total_capitalization` | 10,818 |
| `currentYear_liabilities_total` | 3,191 |
| `avg_equity` | 9,984.18 |
| `avg_total_assets` | 13,346.09 |
| `avg_total_capitalization` | 10,620.18 |

**4.6 Ratio named ranges** — formulas defined in §6; values shown for reference.

| Named range | FY2025 value |
|---|---:|
| `RATIO_market_value_added` | 4,168 |
| `RATIO_market_to_book` | 1.41x |
| `RATIO_eva` | (14) |
| `RATIO_roa_start` | 7.0% |
| `RATIO_roc_start` | 8.9% |
| `RATIO_roe_start` | 8.1% |
| `RATIO_roa_avg` | 6.9% |
| `RATIO_roc_avg` | 8.7% |
| `RATIO_roe_avg` | 7.8% |
| `RATIO_asset_turnover` | 1.05x |
| `RATIO_receivables_turnover` | 5.50x |
| `RATIO_average_collection_period` | 66.4 days |
| `RATIO_inventory_turnover` | 605.77x |
| `RATIO_days_inventory` | 0.6 days |
| `RATIO_profit_margin` | 5.6% |
| `RATIO_operating_profit_margin` | 6.6% |
| `RATIO_long_term_debt_ratio` | 5.1% |
| `RATIO_long_term_debt_equity` | 0.05x |
| `RATIO_total_debt_ratio` | 23.7% |
| `RATIO_times_interest_earned` | 4.92x |
| `RATIO_cash_coverage` | 7.14x |
| `RATIO_debt_burden` | 0.847 |
| `RATIO_leverage` | 1.31x |
| `RATIO_nwc_to_assets` | 52.6% |
| `RATIO_current` | 4.03x |
| `RATIO_quick` | 3.85x |
| `RATIO_cash` | 2.74x |
| `RATIO_roa_dupont` | 7.0% |
| `RATIO_roe_dupont` | 7.8% |

---

### 5. Derived Inputs

All formulas in named-range notation as built in the workbook.

**5.1 Start of Year (Prior-Year Balance Sheet)** — pulled from FY Prior column of §3.1.

| Named range | Formula | Value (KRW bn) |
|---|---|---:|
| `startYear_equity` | =`BAL_equity_shareholders_prior` | 9,705 |
| `startYear_inventory` | =`BAL_inventories_prior` | 19 |
| `startYear_receivables` | =`BAL_receivables_prior` | 2,534 |
| `startYear_total_assets` | =`BAL_assets_total_prior` | 13,238 |
| `startYear_total_capitalization` | =`BAL_debt_long_term_prior` + `BAL_equity_shareholders_prior` | 10,422 |

**5.2 Current Year (Derived)**

| Named range | Formula | Value |
|---|---|---:|
| `currentYear_after_tax_operating_income` | =`INC_net` + (1 − `tax_rate`) × `INC_interest_expense` | 924 |
| `currentYear_daily_sales_average` | =`INC_sales` / 365 | 38.16 |
| `currentYear_equity` | =`BAL_equity_shareholders_curr` | 10,263 |
| `currentYear_cash_marketable_securities` | =`BAL_cash_marketable_securities_curr` | 6,380 |
| `currentYear_assets_current` | =`BAL_assets_current_curr` | 9,406 |
| `currentYear_liabilities_current` | =`BAL_liabilities_current_curr` | 2,332 |
| `currentYear_cost_goods_sold_daily` | =`INC_cost_goods_sold` / 365 | 31.53 |
| `currentYear_debt_long_term` | =`BAL_debt_long_term_curr` | 555 |
| `currentYear_working_capital_net` | =`BAL_assets_current_curr` − `BAL_liabilities_current_curr` | 7,074 |
| `currentYear_assets_total` | =`BAL_assets_total_curr` | 13,454 |
| `currentYear_total_capitalization` | =`currentYear_debt_long_term` + `currentYear_equity` | 10,818 |
| `currentYear_liabilities_total` | =`BAL_liabilities_total_curr` | 3,191 |

**5.3 Mixed Year (Averages)**

| Named range | Formula | Value |
|---|---|---:|
| `avg_equity` | =AVERAGE(`startYear_equity`, `currentYear_equity`) | 9,984.18 |
| `avg_total_assets` | =AVERAGE(`startYear_total_assets`, `currentYear_assets_total`) | 13,346.09 |
| `avg_total_capitalization` | =AVERAGE(`startYear_total_capitalization`, `currentYear_total_capitalization`) | 10,620.18 |

---

### 6. Ratio Definitions & Formulas

Twenty-seven ratios in six categories. Every ratio is expressed in named-range notation as implemented in the workbook. Computed FY2025 values are shown in the rightmost column.

**6.1 Performance (Market Value)**

| Ratio | Named range | Formula | Unit | FY2025 | Interpretation |
|---|---|---|---|---:|---|
| Market value added | `RATIO_market_value_added` | =`market_capitalization` − `currentYear_equity` | KRW bn | 4,168 | Wealth created above book value |
| Market-to-book ratio | `RATIO_market_to_book` | =`market_capitalization` / `currentYear_equity` | x | 1.41x | >1.0x = market values intangibles / growth beyond book |
| Economic value added | `RATIO_eva` | =`currentYear_after_tax_operating_income` − (`cost_capital` × `startYear_total_capitalization`) | KRW bn | **(14)** | **Negative — returns just below 9.0% cost of capital** |

> **Flagged finding:** EVA is slightly negative (−14 KRW bn) despite positive ROC of 8.9%, because the start-of-year invested capital of 10,422 multiplied by the 9.0% cost of capital (938) exceeds the after-tax operating income of 924. Stage 5 must address this in §8 and §10.

**6.2 Profitability**

| Ratio | Named range | Formula | Unit | FY2025 | Interpretation |
|---|---|---|---|---:|---|
| Return on assets (start) | `RATIO_roa_start` | =`currentYear_after_tax_operating_income` / `startYear_total_assets` | % | 7.0% | NOPAT yield on opening assets |
| Return on capital (start) | `RATIO_roc_start` | =`currentYear_after_tax_operating_income` / `startYear_total_capitalization` | % | 8.9% | NOPAT yield on invested capital — **vs `cost_capital` 9.0%** |
| Return on equity (start) | `RATIO_roe_start` | =`INC_net` / `startYear_equity` | % | 8.1% | Net income yield on opening equity |
| Return on assets (avg) | `RATIO_roa_avg` | =`currentYear_after_tax_operating_income` / `avg_total_assets` | % | 6.9% | NOPAT yield on 2-period average assets |
| Return on capital (avg) | `RATIO_roc_avg` | =`currentYear_after_tax_operating_income` / `avg_total_capitalization` | % | 8.7% | NOPAT yield on 2-period average invested capital |
| Return on equity (avg) | `RATIO_roe_avg` | =`INC_net` / `avg_equity` | % | 7.8% | Net income yield on 2-period average equity |

**6.3 Efficiency**

| Ratio | Named range | Formula | Unit | FY2025 | Interpretation |
|---|---|---|---|---:|---|
| Asset turnover | `RATIO_asset_turnover` | =`INC_sales` / `startYear_total_assets` | x | 1.05x | Revenue per KRW of opening assets |
| Receivables turnover | `RATIO_receivables_turnover` | =`INC_sales` / `startYear_receivables` | x | 5.50x | Collection velocity |
| Average collection period | `RATIO_average_collection_period` | =`startYear_receivables` / `currentYear_daily_sales_average` | Days | 66.4 | Days outstanding |
| Inventory turnover | `RATIO_inventory_turnover` | =`INC_cost_goods_sold` / `startYear_inventory` | x | 605.77x | Inventory velocity (extremely high — services business carries minimal inventory) |
| Days in inventory | `RATIO_days_inventory` | =`startYear_inventory` / `currentYear_cost_goods_sold_daily` | Days | 0.6 | <1 day inventory |
| Profit margin | `RATIO_profit_margin` | =`INC_net` / `INC_sales` | % | 5.6% | Bottom-line profitability |
| Operating profit margin (NOPAT) | `RATIO_operating_profit_margin` | =`currentYear_after_tax_operating_income` / `INC_sales` | % | 6.6% | After-tax operating margin |

> **Terminology distinction for Stage 5:** Workbook's `RATIO_operating_profit_margin` = 6.6% is NOPAT/Sales. The Stage 2 memo's "operating margin" 6.9% = `INC_ebit` / `INC_sales` = 957 / 13,930 = 6.87%. Both must be reported and labeled clearly in Stage 5; do not conflate them in the H1 test.

**6.4 Leverage**

| Ratio | Named range | Formula | Unit | FY2025 | Interpretation |
|---|---|---|---|---:|---|
| Long-term debt ratio | `RATIO_long_term_debt_ratio` | =`currentYear_debt_long_term` / (`currentYear_debt_long_term` + `currentYear_equity`) | % | 5.1% | LT debt share of permanent capital |
| Long-term debt-equity | `RATIO_long_term_debt_equity` | =`currentYear_debt_long_term` / `currentYear_equity` | x | 0.05x | Very low |
| Total debt ratio | `RATIO_total_debt_ratio` | =`currentYear_liabilities_total` / `currentYear_assets_total` | % | 23.7% | Total liabilities to assets |
| Times interest earned | `RATIO_times_interest_earned` | =`INC_ebit` / `INC_interest_expense` | x | 4.92x | EBIT coverage of interest |
| Cash coverage ratio | `RATIO_cash_coverage` | =(`INC_ebit` + `INC_depreciation`) / `INC_interest_expense` | x | 7.14x | EBITDA-based interest coverage |
| Debt burden | `RATIO_debt_burden` | =`INC_net` / `currentYear_after_tax_operating_income` | x | 0.847 | Share of NOPAT retained after interest |
| Leverage ratio | `RATIO_leverage` | =`currentYear_assets_total` / `currentYear_equity` | x | 1.31x | Equity multiplier (Du Pont component) |

**6.5 Liquidity**

| Ratio | Named range | Formula | Unit | FY2025 | Interpretation |
|---|---|---|---|---:|---|
| Net working capital to assets | `RATIO_nwc_to_assets` | =`currentYear_working_capital_net` / `currentYear_assets_total` | % | 52.6% | Liquidity buffer scaled by assets |
| Current ratio | `RATIO_current` | =`currentYear_assets_current` / `currentYear_liabilities_current` | x | 4.03x | Short-term solvency |
| Quick ratio | `RATIO_quick` | =(`currentYear_cash_marketable_securities` + `BAL_receivables_curr`) / `currentYear_liabilities_current` | x | 3.85x | Acid test |
| Cash ratio | `RATIO_cash` | =`currentYear_cash_marketable_securities` / `currentYear_liabilities_current` | x | 2.74x | Most conservative |

**6.6 Du Pont System (4-component extended)**

| Component | Named range | Formula | Unit | FY2025 |
|---|---|---|---|---:|
| ROA (Du Pont) | `RATIO_roa_dupont` | =`RATIO_asset_turnover` × `RATIO_operating_profit_margin` | % | 7.0% |
| ROE (Du Pont, extended) | `RATIO_roe_dupont` | =`RATIO_leverage` × `RATIO_asset_turnover` × `RATIO_operating_profit_margin` × `RATIO_debt_burden` | % | 7.8% |

> Verification: `RATIO_roa_dupont` (7.0%) matches `RATIO_roa_start` (7.0%); `RATIO_roe_dupont` (7.8%) matches `RATIO_roe_avg` (7.8%). Workbook marks this with green ✓ "matches direct ROA".

---

### 7. Validation Rules

The model must pass all checks below; any failure invalidates the analysis.

| # | Check | Pass condition | FY2025 result |
|---|---|---|---|
| V1 | Balance Sheet balance — FY2025 | ABS(`BAL_assets_total_curr` − (`BAL_liabilities_total_curr` + `BAL_equity_shareholders_curr`)) < 0.5 | 13,454 = 3,191 + 10,263 = 13,454 ✓ |
| V2 | Balance Sheet balance — FY2024 | ABS(`BAL_assets_total_prior` − (`BAL_liabilities_total_prior` + `BAL_equity_shareholders_prior`)) < 0.5 | 13,238 = 3,533 + 9,705 = 13,238 ✓ |
| V3 | Du Pont reconciliation — ROA | ABS(`RATIO_roa_dupont` − `RATIO_roa_start`) < 0.001 | 7.0% = 7.0% ✓ |
| V4 | Du Pont reconciliation — ROE | ABS(`RATIO_roe_dupont` − `RATIO_roe_avg`) < 0.001 | 7.8% = 7.8% ✓ |
| V5 | Cash Flow reconciliation | `CFS_operating` + `CFS_investing` + `CFS_financing` ≈ `CFS_net_change_cash` | 1,061 − 849 − 367 = (155) ≈ (154) ✓ (±1 KRW bn rounding) |
| V6 | Market cap derivation | `market_capitalization` ≈ `share_price` × `shares_outstanding` | 186,500 × 77M ≈ 14,361 vs workbook 14,431; reconcile via `shares_outstanding` rounded for display (≈ 77.38M underlying) — accept workbook value 14,431 |
| V7 | Memo cross-check — EBIT margin | `INC_ebit` / `INC_sales` ≈ 6.9% (memo Two-Year Snapshot) | 957 / 13,930 = 6.87% ≈ 6.9% ✓ |
| V8 | Effective tax sanity | `INC_taxes` / `INC_taxable_income` ≈ `tax_rate` (workbook assumption 27.3%) | 293 / 1,076 = 27.23% ≈ 27.3% ✓ |
| V9 | Negative-denominator guard | All denominators in §6 > 0 | Pass |

---

## Part B — Analysis Specification

### 8. Analysis Requirements

Stage 5 produces a **structured analytical narrative** for each ratio category, supported by computed values from §6 and benchmarks.

**For every category:**

1. State the FY2025 ratio value (from §6) with named range cited (e.g., `RATIO_current` = 4.03x).
2. Where comparable, state the FY2024 figure (balance-sheet-derived ratios only); else reference the Stage 2 memo Two-Year Snapshot for context.
3. Interpret the directional reading in plain business terms (one to two sentences).
4. Compare to **two benchmark sets**:
   - **Self-vs-hypothesis** — confirm or refute the three hypotheses in §8.1.
   - **Industry peers** — Korean IT services (LG CNS, NAVER Cloud, Lotte Information Communication) and global IT services majors (Accenture, IBM Consulting, Tata Consultancy Services), using most recent full-year ratios.
5. Identify cross-category connections (e.g., high liquidity coexisting with low leverage; asset-light operations lifting asset turnover and ROA together).
6. **Mandatory finding:** Surface the negative EVA (−14 KRW bn) and explain its strategic implication — Samsung SDS's ROC of 8.9% is just below the 9.0% assumed cost of capital, so the company earned marginally less than its cost of capital on FY2025 invested capital.

**8.1 Hypotheses to test (from Stage 2 memo)**

- **H1 Profitability** — Operating margin expands from 6.6% (FY2024) toward 6.8–7.2% (FY2025) driven by higher-margin cloud / digital-transformation mix. **Test:** `INC_ebit` / `INC_sales` = 6.9% lies inside 6.8–7.2% → **H1 confirmed**. Stage 5 must note that workbook's `RATIO_operating_profit_margin` (NOPAT-based, 6.6%) is a different construct than memo's EBIT margin.
- **H2 Efficiency** — IT Services segment asset turnover exceeds Logistics segment asset turnover in FY2025. **Test:** segment disclosures from K-IFRS filings; if segment data unavailable, perform narrative-only assessment and note the limitation explicitly.
- **H3 Liquidity** — Current ratio remains above 3.8x–4.0x in FY2025. **Test:** `RATIO_current` = 4.03x exceeds 4.0x → **H3 confirmed**.

**8.2 Peer benchmark table (Stage 5 must populate)**

| Ratio | Samsung SDS FY2025 | LG CNS | NAVER Cloud | Accenture | TCS | IBM Consulting |
|---|---:|---:|---:|---:|---:|---:|
| EBIT margin | 6.9% | | | | | |
| Net profit margin | 5.6% | | | | | |
| ROE (Du Pont, avg) | 7.8% | | | | | |
| Asset turnover | 1.05x | | | | | |
| Current ratio | 4.03x | | | | | |
| Long-term debt-equity | 0.05x | | | | | |
| Market-to-book | 1.41x | | | | | |

Sources: peer annual reports / Bloomberg / Yahoo Finance, most recent fiscal year available at Stage 5 execution.

---

### 9. Du Pont Decomposition

**Required analysis (4-component extended form):**

1. Compute and state each Du Pont component for FY2025: `RATIO_leverage` (1.31x), `RATIO_asset_turnover` (1.05x), `RATIO_operating_profit_margin` (6.6%), `RATIO_debt_burden` (0.847).
2. Verify `RATIO_roe_dupont` = `RATIO_leverage` × `RATIO_asset_turnover` × `RATIO_operating_profit_margin` × `RATIO_debt_burden` = 7.8%, matching `RATIO_roe_avg`.
3. Identify the **primary driver** of ROE — observe that low `RATIO_leverage` (1.31x vs IT-services norm 1.8–2.5x) is the principal constraint, while `RATIO_operating_profit_margin` and `RATIO_asset_turnover` sit at industry-norm levels.
4. Comment on **sustainability** given Samsung SDS's conservative balance sheet (long-term debt-equity 0.05x).
5. Compare each Du Pont component vs at least one peer (Accenture as global benchmark, LG CNS as Korean benchmark).
6. Conclude: is FY2025 ROE of 7.8% structurally durable, cyclically depressed, or **deliberately under-leveraged** relative to its 9.0% cost of capital?

---

### 10. Strategic Recommendations

Deliver **four** strategic recommendations to Samsung SDS senior finance leadership. Each must meet ALL of:

- **Evidence-grounded** — cites at least two specific named ranges from §6 by exact name.
- **Actionable** — names a specific business lever (not a generality).
- **Quantified** — includes a numeric target or magnitude (target ratio level, KRW amount, % change).
- **Time-bound** — specifies a 12-, 24-, or 36-month horizon.
- **Risk-aware** — acknowledges one trade-off or downside.

**Mandatory coverage (driven by negative-EVA finding):**

1. **Cost-of-capital gap closure (mandatory):** Actions to lift `RATIO_roc_start` from 8.9% above the 9.0% `cost_capital` and turn `RATIO_eva` positive within 24 months. Levers: tactical buybacks reducing equity base; deploying cash into higher-return cloud capex; portfolio rationalization in Logistics.
2. **Capital structure:** Address low `RATIO_leverage` (1.31x) and the KRW 6,380 bn cash position (`currentYear_cash_marketable_securities`).
3. **Working capital:** `RATIO_average_collection_period` 66.4 days is high for an IT-services peer set; compression target.
4. **Investor communication:** Narrative supporting `RATIO_market_to_book` 1.41x in light of negative `RATIO_eva`.

---

### 11. Output Format

Stage 5 deliverable is a single Markdown document, **8–12 pages** rendered, structured as:

| Section | Length | Tone |
|---|---|---|
| Title block + 1-page **Executive Summary** | 1 page | Executive — verdict, three headline ratios, EVA finding, top recommendation |
| §1 Company & Methodology | 0.5 page | Academic — restate company, periods, data sources, ratio framework, naming convention |
| §2 Performance & Market Value | 1 page | Analytical — MVA 4,168; M/B 1.41x; **EVA (14) flagged finding** |
| §3 Profitability | 1.5 pages | Analytical — all 6 profitability ratios + H1 test + EBIT vs NOPAT margin distinction |
| §4 Efficiency & Working Capital | 1.5 pages | Analytical — all 7 efficiency ratios + segment commentary (H2 test) |
| §5 Leverage | 1 page | Analytical — all 7 leverage ratios in context of conservative balance sheet |
| §6 Liquidity | 1 page | Analytical — all 4 liquidity ratios + H3 test |
| §7 Du Pont Decomposition (4-component) | 1 page | Analytical — components, primary driver = low leverage, peer comparison |
| §8 Peer Benchmark Summary | 1 page | Comparative — populated benchmark table + 2-paragraph synthesis |
| §9 Strategic Recommendations | 1.5 pages | Executive — 4 recommendations per §10 criteria; cost-of-capital recommendation mandatory |
| §10 Limitations | 0.25 page | Academic — segment data, single-year IS/CFS, FX exposure, K-IFRS vs IFRS, share-count rounding (V6) |
| References | 0.25 page | Standard |

**Presentation conventions:**

- Every ratio result cited with named range (e.g., "Current ratio (`RATIO_current`) = 4.03x").
- All numeric assertions traceable to a named range or peer source.
- Headings in sentence case.
- Executive summary uses bullet form; analytical body uses prose with embedded tables.
- Negative-EVA finding referenced at least three times: Executive Summary, §2, §9.

---

## References

- Samsung SDS Co., Ltd. *Annual Report 2025*. https://www.samsungsds.com/en/investor/financial_info/about_ir_fif.html
- DART Filing System — Samsung SDS Co., Ltd. K-IFRS Filings. https://dart.fss.or.kr
- Korea Exchange (KRX) — Samsung SDS regulatory disclosures and Dec 30, 2025 last trading day close. https://global.krx.co.kr
- Yahoo Finance — Samsung SDS Co., Ltd. (018260.KS). https://finance.yahoo.com/quote/018260.KS
- Stage 1 ratios template — `models/templates/performance-ratios-template.xlsx`
- Stage 3 populated workbook — `models/builds/2026-05-21-nguyen-samsung-sds-financials.xlsx`
- Stage 2 selection memo — `deliverables/2026-05-18-nguyen-samsung-sds-selection.md`
- Spec template — `https://raw.githubusercontent.com/adamwstauffer/shidler/main/docs/templates/spec-template.md`
- Stage 4 brief — `https://raw.githubusercontent.com/adamwstauffer/shidler/main/courses/BUS-629-VEMBA-International-Corporate-Finance/stage4-technical-specification.md`
