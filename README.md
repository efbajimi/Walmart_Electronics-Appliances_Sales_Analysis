# Walmart Appliance & Electronics Sales Analysis

An end-to-end analytics project on two years of Walmart appliance and electronics
sales. Raw transaction, store, product, and customer tables were cleaned in
**Power Query**, joined into a relational **data model**, summarized with a
**PivotTable**, and visualized in a **Power BI** dashboard.

**Period covered:** Jan 1, 2023 – Dec 31, 2024 · **Scope:** 50 stores · 30 states · 4 regions

---

## Headline numbers

| Metric | Value |
|---|--:|
| Gross revenue | **$6.29M** |
| Gross profit | **$1.80M** |
| Overall margin | **28.6%** |
| Transactions | 5,000 |
| Average order value | $1,258 |
| Products | 50 (Appliances + Electronics) |
| Customers | 1,200 |

### What the data says

- **Electronics outsells Appliances** — $3.49M vs. $2.80M in revenue, and it also
  carries the higher profit ($1.02M vs. $0.78M).
- **The South is the largest region** at $2.40M, followed by West ($1.98M),
  Midwest ($1.25M), and Northeast ($0.66M).
- **California ($838K) and Texas ($705K)** are the top two states by revenue.
- **Top store:** Walmart Neighborhood Market #141 – Raleigh ($188K).
- **Top product:** French Door Refrigerator ($350K), ahead of the Gaming Laptop 16" ($298K).

---

## Project pages

| Page | What's in it |
|---|---|
| **[Data](docs/data.md)** | The four source tables, their schemas, and the cleaning steps |
| **[Pivot Table](docs/pivot-table.md)** | The data model, table relationships, and the PivotTable summary |
| **[Dashboard](docs/dashboard.md)** | The Power BI dashboard and how each visual was built |

## How it was built

1. **Clean** — imported four raw tables into **Power Query** and standardized types, dates, and columns.
2. **Model** — loaded the tables to the Data Model and defined relationships (transactions → stores / products / customers) to form a star schema.
3. **Summarize** — built a **PivotTable** off the model, breaking revenue and profit down by region → state → store and split by product category.
4. **Visualize** — connected the model to **Power BI** and built a one-page dashboard with KPI cards, a regional bar chart, a state choropleth map, and product/store breakdowns.

## Repository structure

```
walmart-sales-analysis/
├── README.md                     # this overview
├── data/
│   ├── transactions.csv          # 5,000 sales transactions (fact table)
│   ├── stores.csv                # 50 stores (dimension)
│   ├── products.csv              # 50 products (dimension)
│   ├── customers.csv             # 1,200 customers (dimension)
│   └── pivot_summary.csv         # exported PivotTable output
├── docs/
│   ├── data.md                   # data page
│   ├── pivot-table.md            # pivot table page
│   └── dashboard.md              # dashboard page
├── assets/
│   ├── dashboard.png             # Power BI dashboard screenshot
│   └── pivot-table.png           # PivotTable screenshot
└── Walmart_data_project.xlsb     # original Excel workbook
```

## Tools

Excel · Power Query · Excel Data Model · PivotTables · Power BI
