# Data

The project is built on **four tables** exported to CSV. Together they form a
star schema: `transactions` is the fact table, and `stores`, `products`, and
`customers` are dimensions that describe it.

The original combined workbook is included as
[`Walmart_data_project.xlsb`](../Walmart_data_project.xlsb).

---

## Cleaning (Power Query)

Each raw table was loaded through Power Query before analysis. The main steps:

- Promoted headers and set explicit data types on every column.
- Converted serial date fields to proper dates (`transaction_date`, `open_date`,
  `launch_date`, `signup_date`).
- Kept revenue/profit fields (`gross_revenue`, `gross_profit`, `margin_pct`, etc.)
  as calculated numeric columns.
- Loaded all four tables to the **Data Model** rather than to worksheets, so they
  could be related and summarized together (see the [Pivot Table page](pivot-table.md)).

---

## Table schemas

### `transactions` — fact table (5,000 rows)

One row per sale. Keys: `customer_id`, `store_id`, `product_id`.

| Column | Description |
|---|---|
| `transaction_id` | Unique transaction key |
| `transaction_date`, `weekday` | Date and day of week |
| `customer_id`, `store_id`, `product_id` | Foreign keys to the dimension tables |
| `quantity`, `unit_price`, `discount_pct` | Line quantity and pricing |
| `gross_revenue`, `discount_amount`, `net_revenue` | Revenue measures |
| `unit_cost`, `gross_profit`, `margin_pct` | Cost and profitability |
| `payment_method`, `channel` | Gift Card / EBT / Debit… and Mobile App / Online / Curbside / In-Store |
| `promotion_applied`, `promotion_type`, `holiday_flag`, `weather_conditions` | Sales context |
| `inventory_level`, `stockout_flag`, `forecasted_demand`, `actual_demand`, `forecast_error` | Inventory & demand |
| `return_flag`, `satisfaction_score` | Post-sale outcomes |

### `stores` — dimension (50 rows)

| Column | Description |
|---|---|
| `store_id` | Primary key |
| `store_name`, `city`, `state`, `region` | Location |
| `store_type` | Supercenter / Discount Store / Neighborhood Market |
| `store_size_sqft`, `employee_count`, `monthly_rent` | Store profile |
| `open_date`, `store_manager`, `remodel_year` | Operational detail |

### `products` — dimension (50 rows)

| Column | Description |
|---|---|
| `product_id` | Primary key |
| `product_name`, `category`, `subcategory`, `brand` | Catalog (category = Appliances / Electronics) |
| `unit_cost`, `list_price` | Pricing |
| `supplier_id`, `supplier_name`, `supplier_lead_time_days` | Supply chain |
| `reorder_point`, `reorder_quantity`, `launch_date`, `active_flag` | Replenishment |

### `customers` — dimension (1,200 rows)

| Column | Description |
|---|---|
| `customer_id` | Primary key |
| `first_name`, `last_name`, `age`, `gender` | Demographics |
| `annual_income`, `household_size` | Household |
| `loyalty_level`, `loyalty_points`, `customer_segment` | Loyalty & segmentation |
| `preferred_channel`, `home_store_id` | Behavior |
| `city`, `state`, `region`, `signup_date`, `email_opt_in` | Location & contact |

---

## Sample — `transactions.csv` (first rows)

| transaction_id | transaction_date | store_id | product_id | quantity | gross_revenue | gross_profit | channel |
|---|---|--:|--:|--:|--:|--:|---|
| 20230001 | 2023-01-30 | 138 | 1011 | 1 | 836.44 | 217.77 | Mobile App |
| 20230002 | 2023-03-10 | 119 | 1015 | 4 | 940.68 | 343.16 | Mobile App |
| 20230003 | 2023-07-21 | 115 | 1027 | 4 | 235.56 | 85.80 | Curbside Pickup |

Full data is in the CSV files linked above.
