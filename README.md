# Retail Executive Dashboard — Tableau Data Storytelling

## Business Problem Summary

A retail leadership team needs a single executive dashboard to monitor sales performance, profitability, customer segments, category performance, shipping performance, discount impact, and return patterns — and to use that view to identify business risks and opportunities, not just look at isolated charts. This project builds that dashboard in Tableau and supports it with a written business story, insights, and chart-selection rationale.

## Dataset Description

**File:** `data/dashboard_sales_data.xlsx`
**Size:** 4,200 orders, 20 columns, covering **January 2024 – December 2025**.

| Field | Description |
|---|---|
| order_id | Unique order identifier |
| order_date / ship_date | Date order was placed / shipped |
| customer_id | Customer identifier |
| customer_segment | Consumer, Corporate, or Home Office |
| region / state / city | Geographic fields |
| category / sub_category / product_name | Product fields |
| ship_mode | Shipping mode used |
| sales / quantity / discount / profit | Order-level numeric measures |
| return_flag | 1 if returned, else 0 |
| delivery_days | Days between order and ship date |
| customer_rating | Customer rating, 1–5 |
| campaign_channel | Acquisition/campaign channel |

A `data_dictionary` sheet with these same field descriptions is included as a second tab inside the Excel file.

## Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`

The workbook contains:
- **7 required analysis sheets:** Sales Trend, Regional Performance View, Category Profitability View, Customer Segment, Shipping Performance, Discount vs Profit View, Return Analysis
- **3 KPI sheets:** KPI Total Sales, KPI Total Profit, KPI Return Rate
- **1 Executive Dashboard** combining the KPIs and 5 of the 7 sheets into a single business-facing view (all 7 analysis sheets exist in the workbook per Task 3; the dashboard itself uses 5, satisfying the "at least 5 charts" requirement in Task 5, while keeping the dashboard layout clean and uncluttered)

## Calculated Fields Created

| Field | Formula | Logic |
|---|---|---|
| Profit Margin | `[profit] / [sales]` | Profit as a share of sales |
| Cost | `[sales] - [profit]` | Implied cost per order |
| Average Order Value | `SUM([sales]) / COUNTD([order_id])` | Average revenue per distinct order |
| Return Rate | `SUM([return_flag]) / COUNTD([order_id])` | Share of orders returned |
| Shipping Delay Bucket | `IF [delivery_days] <= 1 THEN "Same Day/Next Day" ELSEIF [delivery_days] <= 3 THEN "2-3 Days" ELSEIF [delivery_days] <= 5 THEN "4-5 Days" ELSE "6+ Days" END` | Groups raw delivery days into business-readable buckets |

Full explanation and use of each field is in `outputs/business_insights.md` and `outputs/chart_selection_justification.md`.

## Dashboard Components

- **Title banner:** "Retail Executive Dashboard – Sales, Profitability & Risk Overview"
- **3 KPI cards:** Total Sales (₹217,017,652), Total Profit (₹33,306,313), Return Rate (4.55%)
- **5 chart views on the dashboard:** Sales Trend, Regional Performance, Customer Segment, Shipping Performance, Return Analysis
- **Background:** soft neutral shading for a clean, business-friendly look, distinct from chart colors

## Filters and Interactions Used

Filters were added on key dimensions (Region, Customer Segment, Ship Mode) and applied across the relevant worksheets so that selecting a value updates the connected charts together, demonstrating dashboard-wide interactivity rather than single-chart filtering.

## Key Business Insights

Full detail with evidence and recommended actions is in `outputs/business_insights.md`. Headlines:
- Technology category drives 84% of total profit from 71% of sales — the company's profit engine.
- Furniture sells well (₹51.6M) but converts at only 6.9% margin, less than half the company average.
- Profit per order falls sharply as discount increases; orders discounted above 30% are net loss-making as a group.
- Home Office is the highest-value customer segment but also has the highest return rate (5.67%), and Furniture × Home Office specifically has a 9.14% return rate — double the company average.
- 98% of all 6+ day delivery delays come from Standard Class shipping specifically, making it a targeted fix rather than a company-wide one.

## Dashboard Story Summary

Full narrative is in `outputs/dashboard_story.md`. In short: overall performance is healthy (15.35% margin) but growth is flat year-over-year and profitability is concentrated narrowly in the Technology category and a small number of customer/product combinations. The clearest near-term levers are capping deep discounts, fixing Furniture's cost/margin structure, and addressing the Furniture × Home Office return pattern — all backed directly by the dashboard's numbers.

## Assumptions and Limitations

- `customer_rating` had 32 missing values (out of 4,200 rows) with no discernible pattern; left blank rather than imputed, since Tableau's `AVG()` correctly ignores nulls and fabricating ratings would distort the metric.
- `campaign_channel` had 24 missing values, filled with `"Unknown"` so the field remains usable as a clean categorical filter in Tableau (a blank value renders as a confusing "Null" bucket in filters).
- No other data quality issues were found — no duplicate order IDs, no ship dates preceding order dates, and all categorical fields (region, category, segment, etc.) were already consistently spelled/cased in the source file.
- The dataset has no pre-2024 history, so "flat year-over-year growth" is observed only across the two available years and cannot be confirmed as a longer-term trend.
- Return reasons are not captured — the dataset records only whether an order was returned, not why, which limits how directly some return-related recommendations can be acted on without further data collection.

## Screenshots Included

| File | Shows |
|---|---|
| `screenshots/full_dashboard.png` | Complete executive dashboard |
| `screenshots/sales_trend_view.png` | Sales trend chart |
| `screenshots/regional_performance_view.png` | Regional performance view |
| `screenshots/category_profitability_view.png` | Category/sub-category profitability |
| `screenshots/filter_interaction_view.png` | Dashboard with an active filter selection, demonstrating interactivity |
