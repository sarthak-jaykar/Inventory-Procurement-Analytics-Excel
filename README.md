# Inventory & Procurement Operations Analytics — Excel Portfolio Project

## Project overview
An Excel-based operations analytics project for a fictional company, **NexaCore Hardware & Enterprise Supply**. It examines purchase-order spend, supplier delivery reliability, receipt quality, and stock health using synthetic procurement and inventory data.

**Scenario period:** 1 January 2025–15 December 2026  
**Reporting cutoff:** 15 December 2026 (simulated; this is a fictional scenario, not live operational data)

## Business questions
- How much purchasing spend is represented in the cleaned PO population?
- Which suppliers have the highest late-delivery rates?
- What share of received quantity is rejected?
- Which SKU–warehouse combinations are below reorder level or holding excess stock?
- What procurement and inventory actions should operations prioritize?

## Headline results
| KPI | Result | Interpretation |
|---|---:|---|
| Unique purchase orders | 3,500 | After removing 45 duplicate PO records |
| Total PO spend | ₹18,561,536,481 | Sum of unique PO order values |
| Late-delivery rate | 58.94% | Late delivered POs ÷ delivered POs |
| Rejected-quantity rate | 0.60% | Rejected quantity ÷ received quantity |
| Stockout-risk locations | 25 | SKU–warehouse rows below reorder level |
| Excess-stock locations | 20 | SKU–warehouse rows above 120% of target stock |

These are calculated results from the synthetic dataset and the workbook's stated business rules. They are not real company performance figures.

## Key findings and suggested actions
1. **Delivery reliability needs attention.** The overall late-delivery rate is high in this scenario. Review supplier scorecards, confirm the causes of delay, and prioritize SLA discussions or qualified backup suppliers for critical items.
2. **Receipt quality is comparatively stable.** The rejected-quantity rate is 0.60%. Maintain incoming quality checks while investigating whether delays are driven by supplier readiness, transit, or receiving processes.
3. **Inventory is imbalanced across locations.** The workbook flags 25 SKU–warehouse combinations at stockout risk and 20 as excess. Validate demand and transfer options before expediting replenishment or pausing purchases.

## Workbook contents
`Excel Workbook/Inventory_Procurement_Dashboard_Perfected.xlsx` includes:
- `Dashboard` — six headline KPIs and four charts
- `KPI_Calculations` — category-level spend summary
- `Supplier_Analysis` — supplier-level PO, delivery, spend, and rejection metrics
- `Inventory_Analysis` — stock-health counts
- `Cleaned_POs` — deduplicated PO records, standardized status/location fields, lookups, delivery classification, and rejection rate
- `Cleaned_Inventory` — stock health and inventory value by SKU and warehouse
- `Lookups` — supplier and product reference data
- `Methodology_QA` — workbook notes and limitations

`Dataset/Inventory_Procurement_Raw_Dataset.xlsx` contains the raw PO transactions, raw inventory snapshot, product/supplier/warehouse reference tables, and a data-quality log.

## Data quality and methodology
The synthetic raw PO data contains 3,545 rows, including 45 duplicate PO records. The cleaned PO sheet contains 3,500 unique POs. The raw data also includes inconsistent status casing/spacing, warehouse ID trailing spaces, and 30 missing promised delivery dates. The workbook uses Excel formulas such as `TRIM`, `PROPER`, `VLOOKUP`, `XLOOKUP`, `IF`, `COUNTIF/COUNTIFS`, `SUMIF/SUMIFS`, and date calculations to standardize and analyze the data.

Missing promised dates are imputed using the order date plus the supplier's default lead time. Treat these imputed dates as estimates, not observed supplier commitments. Stock-health flags are calculated at the **SKU–warehouse** level:
- **Stockout risk:** available stock < reorder level
- **Excess:** available stock > 120% of target stock
- **Healthy:** neither condition applies

The workbook uses formula-driven summary tables rather than native PivotTables and slicers. The dashboard charts visualize the existing summaries; users can create PivotTables or add slicers manually if required.

## Repository structure
```text
Inventory-Procurement-Analytics-Excel/
├── Dataset/
│   └── Inventory_Procurement_Raw_Dataset.xlsx
├── Excel Workbook/
│   └── Inventory_Procurement_Analytics_Dashboard.xlsx
├── Screenshots/
│   ├── 01-executive-dashboard.png
│   ├── 02-supplier-performance.png
│   ├── 03-cleaned-procurement-data.png
│   ├── 04-inventory-analysis.png
│   ├── 05-kpi-definitions.png
│   └── Business_Requirements_and_KPI_Definitions.md
└── README.md
 
```

## Limitations
- All company, supplier, product, and transaction data is fictional and synthetic.
- The reporting cutoff is part of the simulated scenario and extends into the future relative to the date this portfolio was prepared; it should not be interpreted as current real-world reporting.
- The workbook is designed for Excel recalculation when opened. Verify formula results and chart appearance in your installed spreadsheet application before using screenshots in a portfolio.
- No native PivotTables or slicers are included.

## Tools and skills demonstrated
Microsoft Excel, data cleaning, lookup formulas, conditional logic, procurement KPI design, supplier scorecards, inventory analysis, data-quality handling, dashboarding, and business recommendations.
