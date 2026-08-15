# Dashboard

## What I did

I connected the same relational **data model** to **Power BI** and built a
single-page dashboard for appliance and electronics sales. Because the model's
relationships were already defined, every visual filters and cross-highlights the
others — clicking a region, state, or product reflows the whole page.

## The dashboard

![Power BI dashboard: KPI cards for gross revenue and gross profit, a revenue-by-region bar chart, product and store revenue tables, and a US state map](../assets/dashboard.png)

## Visuals on the page

| Visual | Type | Shows |
|---|---|---|
| Gross Revenue | KPI card | **$6.29M** total revenue |
| Gross Profit | KPI card | **$1.80M** total profit |
| Gross Revenue by Region | Horizontal bar chart | South > West > Midwest > Northeast |
| Product by Revenue | Table | Revenue per product, ranked |
| Gross Revenue by Store | Table | Revenue per store, ranked (Raleigh #141 on top) |
| Gross Revenue by State | Filled US map | Geographic revenue, darkest in CA and TX |

## What it highlights

- **South is the strongest region** and **West is second**, mirroring the PivotTable.
- The **map** makes the coastal concentration obvious — **California and Texas**
  are the darkest states, and much of the interior is unshaded (no stores there).
- The **store table** surfaces the top performers: Raleigh #141, Las Vegas #124,
  and Memphis #129 lead the ranking.

## Design notes

- KPI cards give the two headline numbers immediate visibility.
- The region bar chart is sorted descending so ranking reads at a glance.
- The filled map turns 30 states of store-level data into one quick geographic read.
- Tables stay sortable for anyone who wants to drill into specific products or stores.
