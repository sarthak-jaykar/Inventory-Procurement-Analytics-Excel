# Business Requirements & KPI Definitions

## 1. Business scenario
NexaCore Hardware & Enterprise Supply is a fictional organization used for this portfolio case. The operations team wants a consolidated view of purchase-order spend, supplier delivery performance, receipt quality, and inventory availability across warehouses.

## 2. Objectives
1. Quantify procurement spend using unique purchase orders.
2. Identify suppliers with recurring delivery delays.
3. Measure rejected quantities relative to received quantities.
4. Identify SKU–warehouse combinations that may require replenishment or excess-stock review.
5. Translate the analysis into practical follow-up actions.

## 3. Stakeholders and decisions
- **Procurement manager:** supplier follow-up, SLA review, sourcing alternatives.
- **Warehouse/inventory lead:** stock transfer, replenishment priority, excess-stock review.
- **Quality team:** review rejected receipts and recurring supplier/product issues.
- **Operations leadership:** monitor headline KPIs and agree on action owners.

## 4. KPI definitions
| KPI | Definition | Business rule |
|---|---|---|
| Unique POs issued | Count of unique purchase-order IDs | Count after duplicate PO records are removed |
| Total PO spend | Sum of total order value for unique POs | Uses order value, not cash paid or invoice value |
| Late-delivery rate | Late delivered POs divided by delivered POs | Open POs are excluded from the denominator |
| Rejected-quantity rate | Total rejected quantity divided by total received quantity | Quantity-weighted rate, not an average of PO-level percentages |
| Stockout-risk locations | Count of SKU–warehouse records below reorder level | Available stock < reorder level |
| Excess-stock locations | Count of SKU–warehouse records above 120% of target stock | Available stock > 1.2 × target stock |

## 5. Data assumptions and controls
- All data is synthetic and created for demonstration.
- Duplicate PO records are removed based on PO number.
- Status and warehouse identifiers are standardized by trimming spaces and normalizing status casing.
- Missing promised delivery dates are estimated from order date plus supplier default lead time; these are not actual supplier commitments.
- Inventory flags are calculated per SKU and warehouse, because the same SKU may have different stock levels across locations.
- The scenario's reporting cutoff is 15 December 2026. It is a simulated reporting period, not current operational data.

## 6. Functional requirements
- Present the headline KPIs on one executive dashboard.
- Provide supplier-level metrics for PO volume, open/delivered POs, late delivery, spend, received quantity, and rejected quantity.
- Provide inventory status counts and inventory-level flags.
- Preserve raw source data separately from cleaned analysis sheets.
- Document definitions, assumptions, and limitations so the results can be interpreted consistently.

## 7. Recommended actions
1. Review the supplier scorecard and investigate the causes of late deliveries before renegotiating service levels.
2. Prioritize critical stockout-risk locations after validating demand, lead time, and transfer availability.
3. Review excess-stock locations for transfers, returns, or purchase-order deferral, subject to demand forecasts.
4. Monitor rejection patterns by supplier and product before changing quality-control policy.
