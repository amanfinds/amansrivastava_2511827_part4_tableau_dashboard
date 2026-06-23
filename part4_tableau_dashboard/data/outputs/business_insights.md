# Business Insights — Retail Executive Dashboard

Data period: **January 2024 – December 2025** (24 months, 4,200 orders)

Overall: Total Sales ₹217,017,652 | Total Profit ₹33,306,313 | Overall Profit Margin 15.35% | Overall Return Rate 4.55%

---

## 1. Sales Trend

**Observation:** Monthly sales are volatile but show no sustained growth or decline over the two-year period — the business is essentially flat year-over-year.

**Data evidence:** 2024 monthly sales ranged from ₹6.30M (August) to ₹10.49M (September), averaging ~₹8.85M/month. 2025 monthly sales ranged from ₹7.19M (April) to ₹10.86M (August), averaging ~₹9.23M/month — only a ~4.3% increase year-over-year.

**Business interpretation:** The company is not shrinking, but it is also not scaling. Revenue growth is essentially flat once month-to-month noise is averaged out, which is a concern for a leadership team expecting expansion.

**Recommended action:** Investigate what is driving the recurring mid-year dips (e.g., August 2024) and peaks (September 2024, July–August 2025) — likely seasonal or promotional — and build a deliberate calendar of campaigns around historically strong months instead of leaving performance to chance.

---

## 2. Regional Performance

**Observation:** South is the strongest region on both sales and profit; East and West lag on profit despite comparable sales volume.

**Data evidence:**
| Region | Sales | Profit | Margin |
|---|---|---|---|
| South | ₹64.69M | ₹9.99M | 15.4% |
| North | ₹54.56M | ₹8.31M | 15.2% |
| West | ₹48.91M | ₹7.40M | 15.1% |
| East | ₹48.86M | ₹7.60M | 15.6% |

**Business interpretation:** South generates ~18% more sales than East/West but margins across all four regions are actually very close (15.1%–15.6%) — the real driver of South's lead is sales volume, not regional efficiency. East and West simply need more volume, not a different pricing/discount strategy.

**Recommended action:** Study South's customer acquisition and campaign mix and replicate it in East/West, since margin discipline is already comparable across all regions — the gap is a volume problem, not a profitability problem.

---

## 3. Category / Sub-Category Profitability

**Observation:** Technology dominates company profit; Furniture is the weakest category by margin despite solid sales.

**Data evidence:** Technology: ₹153.9M sales / ₹28.0M profit (18.2% margin). Office Supplies: ₹11.5M sales / ₹1.7M profit (14.9% margin). Furniture: ₹51.6M sales / ₹3.56M profit (only **6.9% margin** — less than half the company average). Top profit sub-categories: Copiers (₹7.31M), Accessories (₹7.19M), Phones (₹7.10M), Machines (₹6.45M). Weakest: Paper, Binders, Storage, Art, Labels — all under ₹370K profit each.

**Business interpretation:** Technology sub-categories are carrying the company's profitability almost single-handedly. Furniture sells well but barely converts that into profit, suggesting either high product cost, heavy discounting, or high return-driven losses in that category (see Insight 8).

**Recommended action:** Conduct a pricing/cost review specifically on Furniture sub-categories (Bookcases, Tables especially) before the next sales push — growing Furniture sales further without fixing margin would not meaningfully help the bottom line.

---

## 4. Customer Segment Behavior

**Observation:** Home Office is the highest-value segment by sales and profit, but also carries the highest return rate by a wide margin.

**Data evidence:**
| Segment | Sales | Profit | Return Rate |
|---|---|---|---|
| Home Office | ₹74.50M | ₹11.56M | **5.67%** |
| Consumer | ₹71.89M | ₹11.03M | 3.91% |
| Corporate | ₹70.63M | ₹10.72M | 4.00% |

**Business interpretation:** Home Office customers are the most commercially valuable segment, but their return rate is ~45% higher than Consumer's. If left unaddressed, return-related costs (reverse logistics, restocking, refunds) will quietly erode the segment's strong profit contribution.

**Recommended action:** Run a root-cause review specifically on Home Office returns — start with the Furniture × Home Office combination (see Insight 8), which is the single worst-performing segment/category pairing in the dataset.

---

## 5. Discount Impact

**Observation:** Profit per order drops sharply and consistently as discount rate increases, turning negative once discounts exceed ~30%.

**Data evidence:**
| Discount Band | Orders | Avg Profit/Order | Total Profit |
|---|---|---|---|
| 0% | 1,024 | ₹13,203 | ₹13.52M |
| 1–10% | 979 | ₹10,010 | ₹9.80M |
| 11–20% | 1,047 | ₹6,336 | ₹6.63M |
| 21–30% | 1,086 | ₹3,181 | ₹3.45M |
| 30%+ | 64 | **–₹1,601** | **–₹102K (net loss)** |

**Business interpretation:** This is one of the clearest and most actionable patterns in the entire dataset. Every step up in discount band reduces average profit per order by roughly half, and orders discounted above 30% are actively loss-making as a group — the company is paying customers to take products, in aggregate, at that discount level.

**Recommended action:** Cap discounts below 30% as a near-term policy, or restrict 30%+ discounts to clearance/dead-stock scenarios where any recovery is better than none — this is not a "maybe," the data shows a near-linear erosion of profit with discount depth.

---

## 6. Shipping / Delivery Performance

**Observation:** Standard Class is both the dominant shipping mode and the only mode meaningfully responsible for long delivery delays.

**Data evidence:** Standard Class accounts for 2,435 of 4,200 orders (58%) and an average delivery time of 4.71 days — more than double Same Day's 0.40 days. Of all orders that took 6+ days to deliver, **654 of 666 (98%)** shipped via Standard Class; only 11 via Second Class and 1 via First Class.

**Business interpretation:** Long delivery delays are not spread across shipping modes — they are almost entirely a Standard Class problem. This makes the fix targeted rather than company-wide: leadership doesn't need to overhaul shipping broadly, just Standard Class logistics specifically.

**Recommended action:** Audit Standard Class carrier performance and warehouse dispatch times; even a modest improvement here would eliminate the vast majority of the company's "6+ day" delivery complaints.

---

## 7. Return Patterns

**Observation:** Returns are concentrated in Furniture, and the Furniture × Home Office combination is the single highest-risk pairing in the dataset.

**Data evidence:** Return rate by category — Furniture: **7.67%**, Office Supplies: 3.65%, Technology: 3.03%. Furniture × Home Office specifically: **9.14% return rate** (37 returns out of 405 orders) — roughly double the company average of 4.55%, and the highest rate of any category/segment combination on the dashboard.

**Business interpretation:** Furniture's return problem isn't generic — it's most acute for Home Office buyers specifically, who are also the company's most valuable segment by sales (Insight 4). This combination is quietly taxing the company's best customer segment.

**Recommended action:** Prioritize a returns root-cause investigation (damage in transit, sizing/fit expectations, product description accuracy) specifically for Furniture items sold to Home Office customers before scaling marketing spend further into that segment.

---

## 8. Business Risk & Opportunity

**Observation:** The company's profitability is structurally concentrated and fragile — a small set of dependencies (Technology category, Standard Class shipping, discount discipline) are doing most of the work, and each has a visible crack.

**Data evidence:** Technology alone generates 84% of total company profit (₹28.0M of ₹33.3M) despite being only 71% of sales — meaning two other categories (Furniture, Office Supplies) combine to contribute just ~16% of profit from ~29% of sales. Simultaneously, Organic channel drives the largest share of sales (₹88.8M from 1,694 orders) — more than Paid, Email, and Social combined — indicating limited paid-channel efficiency or under-investment in paid acquisition.

**Business interpretation:** This is both a risk and an opportunity. **Risk:** if Technology demand softens, there is no comparably profitable category to absorb the impact, since Furniture and Office Supplies are running thin margins. **Opportunity:** Organic channel is already outperforming paid channels on volume — there may be room to convert some of that organic strength into a more deliberate retention/loyalty program, or alternatively, the heavy reliance on Organic suggests paid channels are underutilized and could be scaled with confidence given Organic's proven demand.

**Recommended action / follow-up question:** Leadership should ask: *"If Technology category demand dropped 15% next year, what would happen to total company profit, and do we have a plan to diversify profit sources before that risk materializes?"*

---

*All figures above are computed directly from `dashboard_sales_data.xlsx` (4,200 orders, Jan 2024–Dec 2025) via the calculated fields and aggregations built into `executive_dashboard.twbx`.*
