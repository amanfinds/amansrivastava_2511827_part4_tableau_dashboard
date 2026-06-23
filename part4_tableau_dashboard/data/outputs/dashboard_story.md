# Dashboard Story — Retail Executive Dashboard

*A leadership-level narrative, written to connect what the dashboard shows rather than describe each chart in isolation.*

---

## Executive Summary

Over the last two years, the business has generated **₹217M in sales** and **₹33.3M in profit** (a 15.35% overall margin), with a **4.55% return rate**. The headline number is healthy, but it is being carried by a narrow base: one category, one shipping mode, and a small number of customer/product combinations are responsible for most of the risk and most of the opportunity hiding underneath that top-line figure. Sales growth between 2024 and 2025 was essentially flat (~4% YoY), which means the next phase of growth has to come from fixing structural leaks rather than simply "selling more."

## What Is Performing Well

**Technology is the profit engine of the business.** It generates 71% of sales but 84% of profit (₹28.0M of the company's ₹33.3M total), led by Copiers, Accessories, Phones, and Machines — each contributing over ₹6.4M in profit individually. South region leads on absolute performance (₹64.7M sales, ₹9.99M profit), and importantly, profit margins are consistent across all four regions (15.1%–15.6%), which tells us the company's pricing and cost discipline is sound everywhere — South's edge is volume, not efficiency. The Home Office customer segment is also the single most valuable segment by both sales and profit, ahead of Consumer and Corporate.

## What Is Underperforming

**Furniture is selling well but not earning well.** Despite ₹51.6M in sales — the second-largest category — Furniture converts that into only a 6.9% margin, less than half the company average, and well behind Technology's 18.2%. Several Office Supplies sub-categories (Paper, Binders, Storage, Art, Labels) are also structurally low-profit, though not loss-making. Growth in these categories without a pricing or cost fix would add revenue without meaningfully moving the bottom line.

## Risks Visible in the Data

Three risks stand out, and they connect to each other:

1. **Discount depth is actively destroying profit.** Profit per order falls by roughly half with every step up in discount band, and orders discounted above 30% are net loss-making as a group (–₹1,601 average profit/order, –₹102K total). This is not a soft trend — it is one of the clearest, most linear patterns on the entire dashboard.
2. **Returns are concentrated exactly where the company can least afford them.** Furniture has the highest return rate of any category (7.67%), and the Furniture × Home Office combination — the company's single most valuable customer segment — has a 9.14% return rate, roughly double the company average.
3. **Shipping delay risk is a single-point problem.** 98% of all orders that took 6+ days to deliver shipped via Standard Class, which also happens to be the most-used shipping mode (58% of all orders). A logistics issue with Standard Class would touch the majority of the customer base.

## Opportunities Visible in the Data

The flip side of "Technology carries the company" is that **the company has real headroom in Furniture and Office Supplies** if margin issues are addressed — these categories already have sales volume, so a cost or pricing fix would convert existing revenue into new profit without needing new customers. Separately, **Organic acquisition is already outperforming every paid channel** (₹88.8M in sales vs. ₹40.1M from Paid, the next-largest channel) — this is a sign of either strong brand pull or under-investment in paid channels, and either reading points toward a growth lever leadership hasn't fully pulled yet.

## Recommended Business Actions

1. **Cap discounts below 30%** as a default policy, reserving deeper discounts only for clearance/dead-stock situations.
2. **Investigate Furniture's cost structure**, especially Bookcases and Tables, before investing further marketing spend into growing Furniture sales.
3. **Open a root-cause review into Furniture × Home Office returns** — this single combination is quietly taxing the company's best customer segment.
4. **Audit Standard Class shipping operations specifically** — fixing this one mode would resolve the large majority of long-delivery complaints without touching other shipping modes.
5. **Test increased investment in paid channels**, using Organic's strong performance as evidence that demand exists and a paid push may convert efficiently.

## Limitations of This Dashboard

- The dataset covers 24 months (Jan 2024–Dec 2025) with no prior-year baseline, so "flat" year-over-year growth cannot be distinguished from a longer-term trend without older data.
- `customer_rating` has some missing values (left blank, not imputed) — average rating figures should be read as based on available responses only, not 100% of orders.
- Return reasons are not captured in the dataset (only a binary returned/not-returned flag) — the dashboard can show *where* returns concentrate but not *why*, which limits how directly Insight 7's recommendation can be acted on without further data collection.
- Profit and discount figures are net company numbers; the dashboard does not break out fixed vs. variable cost components, so "margin" here reflects what the dataset's `profit` field already nets out, not a full cost-accounting view.

## Suggested Next Analysis

A focused deep-dive on **Furniture returns** (with reason codes, if collected going forward) and a **discount-elasticity test** — deliberately varying discount depth in a controlled way for a subset of products — would convert this dashboard's "what happened" view into a "what should we do next" experiment, directly targeting the two clearest risk areas identified here.
