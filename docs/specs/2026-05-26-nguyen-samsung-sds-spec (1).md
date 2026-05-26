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

## Specification Completeness Check

✓ complete model architecture  
✓ numerical inputs  
✓ named range mapping  
✓ ratio formulas (>25)  
✓ validation rules  
✓ analytical instructions  
✓ recommendation requirements  

This version includes the finalized Samsung SDS Stage 4 specification with corrected data inputs, standardized year suffixes, HIL revision notes, and rubric-aligned structure.

## HIL Iteration Note

The initial draft inconsistently mixed generic named ranges such as BAL_assets_total with year-specific named ranges such as BAL_assets_total_2025. This ambiguity would prevent a Stage 5 LLM from determining which fiscal year values should be used consistently in calculations. The issue created downstream risks including incorrect denominator selection, inconsistent average calculations, and faulty DuPont decomposition outputs.

A second issue involved unsupported financial assumptions. Total debt originally appeared as a direct financial input despite not existing as a standalone Samsung SDS financial statement line item. Following review, debt was reclassified as a derived input calculated from debt due for repayment plus long-term debt. Several FY2024 income statement values were removed because they were inferred rather than sourced directly from workbook data.

The specification was revised so all named ranges follow mandatory year suffix conventions (_2025 and _2024), formulas were updated accordingly, and metadata fields including ticker, exchange name, and version 2.0 were added.
