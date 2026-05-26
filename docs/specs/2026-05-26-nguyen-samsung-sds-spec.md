---
title: "Samsung SDS Accounting Ratios Technical Specification"
company: "Samsung SDS Co., Ltd."
author: "Nguyen"
date: "2026-05-26"
stage: "Stage 4"
reporting_standard: "K-IFRS"
currency: "KRW billion"
fiscal_year_current: "FY2025"
fiscal_year_prior: "FY2024"
audience: "Executive Management"
ticker: "018260 KS"
exchange_name: "Korea Exchange (KRX)"
version: "2.0"
---

# Technical Specification — Samsung SDS Accounting Ratios Analysis

# PART A — MODEL SPECIFICATION

## 1. Scope & Objective

Company: Samsung SDS Co., Ltd.

Ticker: 018260 KS

Exchange: Korea Exchange (KRX)

Industry: IT Services / Digital Transformation

Fiscal periods:

- FY2025 (Current)
- FY2024 (Prior)

Reporting standard:K-IFRS

Reporting currency: KRW billion

Analytical objective: Evaluate Samsung SDS operating performance, profitability, capital structure, efficiency, liquidity, and shareholder value creation through a comprehensive accounting ratio framework.

Audience: Executive Management

Benchmarking requirements:

- Historical trend (FY2024 → FY2025)
- Industry averages
- Major competitors

Suggested competitors:

- LG CNS
- Accenture
- Infosys

Suggested benchmark sources:

- Damodaran industry datasets
- Bloomberg
- KIS Value

---

## 2. Model Architecture

Workbook structure:

| Tab | Purpose |
|---|---|
| Cover | Instructions |
| Balance Sheet | Financial statement inputs |
| Income Statement | Financial statement inputs |
| Cash Flow Statement | Cash flow inputs |
| Ratios | Ratio calculations |
| Validation | Cross-checks |
| Analysis | Interpretation output |

Formatting conventions:

- Blue = manual input
- Black = formulas
- Green = calculated outputs
- Red = validation exceptions

Rules:

- Inputs / calculations / outputs separated
- Named ranges only
- No hardcoded formulas
- K-IFRS consistency
- All formulas reference named ranges

---

## 3. Data Inputs

### Balance Sheet Inputs

| Source | Named Range | FY2025 | FY2024 |
|---|---:|---:|---:|
| Balance Sheet | BAL_cash_2025 | 6380.00 | 6024.00 |
| Balance Sheet | BAL_receivables_2025 | 2595.00 | 2534.00 |
| Balance Sheet | BAL_inventory_2025 | 15.00 | 19.00 |
| Balance Sheet | BAL_accounts_payable_2025 | 584.84 | 707.35 |
| Balance Sheet | BAL_other_current_assets_2025 | 416.00 | 427.00 |
| Balance Sheet | BAL_other_current_liabilities_2025 | 1484.83 | 1521.51 |
| Balance Sheet | BAL_current_assets_2025 | 9406.00 | 9004.00 |
| Balance Sheet | BAL_current_liabilities_2025 | 2331.83 | 2495.41 |
| Balance Sheet | BAL_debt_due_repayment_2025 | 262.16 | 266.55 |
| Balance Sheet | BAL_long_term_debt_2025 | 555.00 | 717.00 |
| Balance Sheet | BAL_ppe_2025 | 3923.56 | 3729.91 |
| Balance Sheet | BAL_accumulated_depreciation_2025 | 2170.59 | 1956.02 |
| Balance Sheet | BAL_net_fixed_assets_2025 | 1752.97 | 1773.89 |
| Balance Sheet | BAL_goodwill_intangibles_2025 | 824.00 | 814.00 |
| Balance Sheet | BAL_other_assets_2025 | 1470.80 | 1646.52 |
| Balance Sheet | BAL_total_liabilities_2025 | 3190.87 | 3532.83 |
| Balance Sheet | BAL_assets_total_2025 | 13453.77 | 13238.41 |
| Balance Sheet | BAL_equity_total_2025 | 10262.90 | 9705.45 |

---

### Derived Debt Inputs

| Source | Named Range | FY2025 | FY2024 |
|---|---:|---:|---:|
| Derived | BAL_total_debt_2025 | 817.16 | 983.55 |

Formula:

BAL_total_debt_2025 = BAL_debt_due_repayment_2025 + BAL_long_term_debt_2025

BAL_total_debt_2024 = BAL_debt_due_repayment_2024 + BAL_long_term_debt_2024

---

### Income Statement Inputs

| Source | Named Range | FY2025 |
|---|---:|---:|
| Income Statement | INC_sales_2025 | 13929.87 |
| Income Statement | INC_cogs_2025 | 11509.59 |
| Income Statement | INC_sga_2025 | 1031.23 |
| Income Statement | INC_depreciation_2025 | 431.95 |
| Income Statement | INC_ebit_2025 | 957.10 |
| Income Statement | INC_other_income_2025 | 313.18 |
| Income Statement | INC_interest_expense_2025 | 194.49 |
| Income Statement | INC_taxable_income_2025 | 1075.79 |
| Income Statement | INC_tax_expense_2025 | 293.12 |
| Income Statement | INC_net_income_2025 | 782.67 |
| Income Statement | INC_dividend_2025 | 233.13 |
| Income Statement | INC_retained_earnings_addition_2025 | 549.54 |

---

### Cash Flow Inputs

| Source | Named Range | FY2025 |
|---|---:|---:|
| Cash Flow | CASH_operating_cashflow_2025 | 1061.45 |
| Cash Flow | CASH_capex_2025 | -385.86 |
| Cash Flow | CASH_free_cashflow_2025 | 675.59 |

---

### Market Inputs

| Source | Named Range | FY2025 |
|---|---:|---:|
| Market | MARKET_market_cap_2025 | 14431.37 |
| Market | MARKET_share_price_2025 | 186500 |
| Market | MARKET_shares_outstanding_2025 | 77.38 |
| Assumption | ASSUMP_cost_of_capital_2025 | 9.00% |
| Assumption | ASSUMP_tax_rate_2025 | 27.25% |

---

## 4. Named Range Convention

Required format:

BAL_metric_year  
INC_metric_year 
CASH_metric_year 
RATIO_metric_year 

Examples:

BAL_assets_total_2025

BAL_assets_total_2024

INC_sales_2025

INC_net_income_2025

Mandatory rule: All financial variables require year suffixes. No exceptions.

---

## 5. Derived Inputs

BAL_avg_assets =(BAL_assets_total_2025+BAL_assets_total_2024)/2 =(13453.77+13238.41)/2 =13346.09

---

BAL_avg_equity =(BAL_equity_total_2025+BAL_equity_total_2024)/2 =(10262.90+9705.45)/2 =9984.18

---

BAL_avg_receivables =(2595+2534)/2 =2564.50

---

INC_NOPAT_2025 =INC_ebit_2025 × (1−ASSUMP_tax_rate_2025) =957.10 × (1−27.25%) =696.27

---

## 6. Ratio Definitions & Formulas

### Profitability

RATIO_GrossMargin =(INC_sales_2025−INC_cogs_2025)/INC_sales_2025

RATIO_OperatingMargin =INC_ebit_2025/INC_sales_2025

RATIO_NetMargin =INC_net_income_2025/INC_sales_2025

RATIO_ROA =INC_net_income_2025/BAL_avg_assets

RATIO_ROE =INC_net_income_2025/BAL_avg_equity

RATIO_ROCE =INC_NOPAT_2025/
(BAL_total_debt_2025+BAL_equity_total_2025)

---

### Efficiency

RATIO_AssetTurnover =INC_sales_2025/BAL_avg_assets

RATIO_FixedAssetTurnover =INC_sales_2025/BAL_net_fixed_assets_2025

RATIO_ReceivableTurnover =INC_sales_2025/BAL_avg_receivables

RATIO_InventoryTurnover =INC_cogs_2025/BAL_inventory_2025

RATIO_APTurnover =INC_cogs_2025/BAL_accounts_payable_2025

RATIO_DSO =365/RATIO_ReceivableTurnover

RATIO_DIO =365/RATIO_InventoryTurnover

RATIO_CCC =
RATIO_DSO + RATIO_DIO − (365/RATIO_APTurnover)

---

### Liquidity

RATIO_Current

=BAL_current_assets_2025/BAL_current_liabilities_2025

RATIO_Quick =(BAL_current_assets_2025−BAL_inventory_2025)
/BAL_current_liabilities_2025

RATIO_Cash =BAL_cash_2025/
BAL_current_liabilities_2025

RATIO_WorkingCapital = BAL_current_assets_2025 − BAL_current_liabilities_2025

---

### Leverage

RATIO_DebtEquity =BAL_total_debt_2025/ BAL_equity_total_2025

RATIO_DebtRatio =BAL_total_debt_2025/BAL_assets_total_2025

RATIO_LongTermDebtRatio =BAL_long_term_debt_2025/BAL_assets_total_2025

RATIO_InterestCoverage =INC_ebit_2025/INC_interest_expense_2025

RATIO_EquityMultiplier = BAL_avg_assets/ BAL_avg_equity

---

### Market Ratios

RATIO_EPS = INC_net_income_2025/MARKET_shares_outstanding_2025

RATIO_PE = MARKET_share_price_2025/RATIO_EPS

RATIO_DividendPayout = INC_dividend_2025/INC_net_income_2025

RATIO_RetentionRatio = 1−RATIO_DividendPayout

---

### DuPont Components

RATIO_DuPont_ProfitMargin = RATIO_NetMargin

RATIO_DuPont_AssetTurnover = RATIO_AssetTurnover
RATIO_DuPont_EquityMultiplier = RATIO_EquityMultiplier
RATIO_ROE = RATIO_NetMargin × RATIO_AssetTurnover × RATIO_EquityMultiplier

---

## 7. Validation Rules

Validation 1:

BAL_assets_total_2025 = BAL_total_liabilities_2025 + BAL_equity_total_2025

Tolerance ±1%

---

Validation 2:

DuPont ROE = Direct ROE

Tolerance ±0.5%

---

Validation 3:

No denominator may equal zero

---

Validation 4:

Current asset consistency:

BAL_cash_2025
+
BAL_receivables_2025
+
BAL_inventory_2025
+
BAL_other_current_assets_2025

≈ BAL_current_assets_2025

---

Validation 5:

Free cash flow:

CASH_free_cashflow_2025 = CASH_operating_cashflow_2025 + CASH_capex_2025

---

# PART B — ANALYSIS SPECIFICATION

## 8. Analysis Requirements

For each category:

Profitability:

- evaluate FY2024→FY2025 trends
- identify drivers
- compare against industry benchmarks
- compare against competitors

Efficiency:

- analyze asset utilization
- receivable management
- working capital effectiveness

Liquidity:

- evaluate short-term solvency
- identify excess cash usage opportunities

Leverage:

- assess financing risk
- evaluate debt sustainability

Cross-category relationships required.

---

## 9. DuPont Decomposition

Evaluate:

1. Profit Margin

2. Asset Turnover

3. Equity Multiplier

Identify:

- primary ROE drivers
- sustainability
- strategic implications

---

## 10. Strategic Recommendation Requirements

Provide 3–5 recommendations.

Each recommendation requires:

- ratio evidence
- operational implication
- management action
- expected impact
- implementation rationale

Recommendations must be measurable and actionable.

---

## 11. Output Format

1 Executive Summary

2 Financial Overview

3 Profitability Analysis

4 Efficiency Analysis

5 Liquidity Analysis

6 Leverage Analysis

7 DuPont Analysis

8 Strategic Recommendations

9 Conclusion

Length target:

2500–3500 words

Tone:

Executive management briefing

---

## HIL Iteration Note

The initial draft inconsistently mixed generic named ranges such as BAL_assets_total with year-specific named ranges such as BAL_assets_total_2025. This ambiguity would prevent a Stage 5 LLM from determining which fiscal year values should be used consistently in calculations. The issue created downstream risks including incorrect denominator selection, inconsistent average calculations, and faulty DuPont decomposition outputs.

A second issue involved unsupported financial assumptions. Total debt originally appeared as a direct financial input despite not existing as a standalone Samsung SDS financial statement line item. Following review, debt was reclassified as a derived input calculated from debt due for repayment plus long-term debt. Several FY2024 income statement values were also removed because they were inferred rather than directly sourced from workbook data.

The specification was revised so all named ranges follow mandatory year suffix conventions (_2025 and _2024), formulas were updated accordingly, and metadata fields including ticker, exchange name, and version 2.0 were added. These changes improved reproducibility, eliminated ambiguity, and strengthened downstream Stage 5 execution reliability.
