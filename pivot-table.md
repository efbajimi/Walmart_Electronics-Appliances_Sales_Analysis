# Pivot Table

## What I did

The four cleaned tables were loaded into the **Excel Data Model** instead of
plain worksheets. Inside the model I defined **relationships** so a single
PivotTable could pull from all of them at once:

```
transactions.store_id     →  stores.store_id
transactions.product_id   →  products.product_id
transactions.customer_id  →  customers.customer_id
```

This is a **star schema**: `transactions` is the fact table in the middle, and
`stores`, `products`, and `customers` are dimensions hanging off it. The
relationships let the PivotTable slice transaction measures by any attribute of a
related table — for example, revenue by a store's **region** or by a product's
**category** — without any lookup formulas.

With the model in place I built a PivotTable to summarize **Gross Revenue** and
**Gross Profit**:

- **Rows** — a drill-down hierarchy of **Region → State → Store** (from `stores`).
- **Columns** — product **Category** (Appliances vs. Electronics, from `products`),
  each split into Gross Revenue and Gross Profit.
- **Values** — `Sum of gross_revenue` and `Sum of gross_profit` from `transactions`,
  plus grand-total columns for each.

The full export is in [`data/pivot_summary.csv`](../data/pivot_summary.csv).

## The PivotTable

![PivotTable summarizing revenue and profit by region, state, and store, split by product category](../assets/pivot-table.png)

## Region-level summary

Collapsed to the region level, the PivotTable reads:

| Region | Appliances Rev | Appliances Profit | Electronics Rev | Electronics Profit | Total Rev | Total Profit |
|---|--:|--:|--:|--:|--:|--:|
| Northeast | $286,838 | $81,090 | $372,800 | $110,266 | $659,637 | $191,355 |
| Midwest | $552,300 | $153,442 | $695,856 | $202,614 | $1,248,156 | $356,056 |
| West | $882,340 | $248,649 | $1,097,570 | $324,073 | $1,979,910 | $572,722 |
| South | $1,082,035 | $294,081 | $1,321,271 | $387,579 | $2,403,306 | $681,660 |
| **Grand Total** | **$2,803,512** | **$777,261** | **$3,487,498** | **$1,024,531** | **$6,291,010** | **$1,801,792** |

## Readings

- **Electronics beats Appliances in every region** on both revenue and profit.
- **The South leads** at $2.40M total revenue — more than the Midwest and
  Northeast combined.
- Grand totals reconcile exactly with the dashboard: **$6,291,010 revenue** and
  **$1,801,792 profit**.
