# Chart Selection Justification

For each major view in the executive dashboard, this document explains the business question it answers, why the chart type fits that question, what's mapped to which visual channel, the design principle applied, and the mistake it avoids.

---

## 1. Sales Trend

- **Question answered:** How are sales changing over time?
- **Why this chart type:** A line chart is the standard choice for time-series data because the connecting line lets the eye follow direction and rate of change month over month — something a bar chart or table would not show as intuitively.
- **Field mapping:** Columns = `MONTH(Order Date)`, Rows = `SUM(Sales)`. No color/size encoding — kept single-series for clarity.
- **Design principle applied:** Minimal clutter — a single clean line with no unnecessary gridlines, dual axes, or secondary metrics competing for attention.
- **Mistake avoided:** Did not default to a yearly aggregation (which would have collapsed 24 months into just 2 data points and hidden all seasonal variation) — explicitly used Month-level granularity instead.

---

## 2. Regional Performance View

- **Question answered:** Which region performs best, on both sales and profit?
- **Why this chart type:** A horizontal bar chart ranks categorical values (regions) by a single measure (sales) in a way that's instantly scannable — longer bar = higher sales, no decoding required.
- **Field mapping:** Rows = `Region`, Columns = `SUM(Sales)`, Color = `SUM(Profit)` (diverging red-to-green palette).
- **Design principle applied:** Dual-encoding for added context without adding a second chart — color carries a second metric (profit) on top of the bar length (sales), letting one chart answer two related questions at once.
- **Mistake avoided:** Avoided defaulting to a sequential single-hue gradient (e.g., light-to-dark green only), which made low-profit regions nearly invisible against a white background in an earlier draft. Switched to a diverging red-green palette so underperforming regions are immediately visually distinct, not just slightly lighter.

---

## 3. Category Profitability View

- **Question answered:** Which categories and sub-categories drive profit or losses?
- **Why this chart type:** A nested bar chart (Category → Sub-Category) shows both the high-level grouping and the granular detail in one view, which a flat bar chart of 17 sub-categories alone would not communicate as clearly.
- **Field mapping:** Columns = `Category` nested with `Sub-Category`, Rows = `SUM(Profit)`, Color = `SUM(Profit)` (gradient, negative values reading as red/orange).
- **Design principle applied:** Hierarchy — the Category/Sub-Category nesting mirrors how leadership actually thinks about the product catalog, from broad to specific, rather than flattening everything into one undifferentiated list.
- **Mistake avoided:** Avoided plotting raw per-order profit marks (which initially rendered as dozens of thin stacked stripes per bar instead of one solid bar) — corrected the Marks type to Bar so each sub-category renders as a single clean, readable bar.

---

## 4. Customer Segment View

- **Question answered:** How does performance compare across customer segments, and where is return risk concentrated?
- **Why this chart type:** A simple bar chart per segment, augmented with a return-rate label, answers "which segment is best" and "which segment is riskiest" in a single glance — appropriate since there are only 3 categories to compare.
- **Field mapping:** Columns = `Customer Segment`, Rows = `SUM(Sales)`, Color = `SUM(Profit)`, Label = `Return Rate` (formatted as %).
- **Design principle applied:** Business interpretation over decoration — the return rate label was added specifically because sales/profit alone would have hidden the fact that the highest-performing segment (Home Office) is also the highest-risk one.
- **Mistake avoided:** Avoided leaving Return Rate as a raw decimal (e.g., 0.0567) on the label, which would have required leadership to mentally convert to a percentage — formatted it explicitly as % during construction.

---

## 5. Shipping Performance View

- **Question answered:** Which shipping mode causes delivery delay?
- **Why this chart type:** A highlight table (heatmap) is the right choice for two categorical dimensions (Ship Mode × Delay Bucket) crossed with a count measure — color intensity makes the concentration of orders in each cell immediately visible without needing to read every number.
- **Field mapping:** Rows = `Ship Mode`, Columns = `Shipping Delay Bucket` (calculated field), Color = `CNTD(Order Id)`, Label = `CNTD(Order Id)`.
- **Design principle applied:** Appropriate sorting/structure for cross-tabulation — using a calculated field (Shipping Delay Bucket) to create meaningful, business-readable buckets (e.g., "6+ Days") instead of showing raw, unbucketed delivery-day numbers that would be harder to scan.
- **Mistake avoided:** Avoided using `SUM(Order Id)` (meaningless for an ID field) — explicitly switched the aggregation to Count Distinct so each order is counted exactly once.

---

## 6. Discount vs Profit View

- **Question answered:** How does discount level relate to profit?
- **Why this chart type:** A scatter plot is the correct choice for examining the relationship between two continuous numeric variables (discount, profit) at the individual order level — a bar or line chart would have forced unwanted aggregation and hidden the spread/variance visible here.
- **Field mapping:** Columns = `Discount`, Rows = `Profit`, Color = `Category`, Detail = `Order Id` (kept at row-level granularity, not aggregated).
- **Design principle applied:** Correct level of detail for the question — `Order Id` was deliberately placed on Detail so each mark represents one real order rather than a category average, which preserves the visible pattern of profit eroding (and eventually going negative) as discount increases.
- **Mistake avoided:** Avoided accidentally aggregating Discount and Profit to `SUM()` at the chart level, which would have collapsed thousands of individual orders into a single misleading point — confirmed Order Id on Detail keeps the view at per-order granularity.

---

## 7. Return Analysis

- **Question answered:** Which category/segment combination has the highest return risk?
- **Why this chart type:** A nested bar chart (Category → Customer Segment) directly compares return rate across every combination of the two dimensions leadership cares about most, surfacing the single worst combination (Furniture × Home Office) without needing a separate cross-tab table.
- **Field mapping:** Columns = `Category` nested with `Customer Segment`, Rows = `Return Rate` (calculated field, formatted as %), Color = `Customer Segment`.
- **Design principle applied:** Consistent color usage — `Customer Segment` color coding here matches the same segment colors used on the Customer Segment View, so leadership can visually connect the two charts without re-learning a new color key.
- **Mistake avoided:** Avoided showing return counts instead of return rate, which would have misleadingly favored categories with fewer total orders — used the `Return Rate` calculated field (returns ÷ distinct orders) specifically to make the comparison fair across categories/segments of different sizes.

---

## 8. KPI Cards (Total Sales, Total Profit, Return Rate)

- **Question answered:** What are the headline numbers leadership needs before looking at any detail chart?
- **Why this chart type:** A single large text number is the simplest possible visual for a top-line metric — no chart type communicates "the one number that matters" faster than a number itself.
- **Field mapping:** Each KPI is a single aggregated measure (`SUM(Sales)`, `SUM(Profit)`, `Return Rate`) placed on Text, with no other encoding.
- **Design principle applied:** Hierarchy/visual priority — placed at the very top of the dashboard, in the largest font on the page, so they are the first thing read before any chart.
- **Mistake avoided:** Avoided combining all 3 KPIs into one crowded card or table — kept each as its own clean card so no single number competes visually with another.
