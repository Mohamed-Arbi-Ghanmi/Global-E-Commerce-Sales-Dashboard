# Data Dictionary — superstore_clean.csv

27 columns. All columns from the raw file are kept except `Row ID` (dropped — redundant sequential index) and `Country` (dropped — single value: "United States").

---

## Original Columns (retained)

| Column | Type | Description |
|---|---|---|
| Order ID | string | Unique identifier per order. Multiple rows can share an Order ID (one row per product line). |
| Order Date | datetime | Date the order was placed. |
| Ship Date | datetime | Date the order was shipped. |
| Ship Mode | string | Shipping method chosen: `Same Day`, `First Class`, `Second Class`, `Standard Class`. |
| Customer ID | string | Unique customer identifier. |
| Customer Name | string | Full name of the customer. |
| Segment | string | Customer segment: `Consumer`, `Corporate`, or `Home Office`. |
| City | string | City of the shipping address. |
| State | string | US state of the shipping address. |
| Postal Code | string | 5-character US ZIP code. **Note:** raw file stored this as integer, which stripped leading zeros (e.g. `01040` → `1040`). Zero-padding was applied in ETL to restore correct values. |
| Region | string | US sales region: `East`, `West`, `Central`, or `South`. |
| Product ID | string | Unique product identifier. |
| Category | string | Top-level product category: `Furniture`, `Office Supplies`, or `Technology`. |
| Sub-Category | string | Product sub-category (17 values, e.g. `Chairs`, `Phones`, `Binders`). |
| Product Name | string | Full product name. |
| Sales | float | Revenue for the line item in USD. |
| Quantity | int | Number of units ordered. |
| Discount | float | Discount applied as a decimal (0.0 = no discount, 0.8 = 80% off). |
| Profit | float | Net profit for the line item in USD. Can be negative. |

---

## Derived Columns (added in ETL)

| Column | Type | Description |
|---|---|---|
| Year | int | Order year extracted from `Order Date` (2014–2017). |
| Month | int | Order month as integer (1–12). |
| Quarter | string | Order quarter: `Q1`, `Q2`, `Q3`, or `Q4`. |
| Year-Month | string | Order year and month in `YYYY-MM` format (e.g. `2016-11`). Useful for time-series grouping in Looker Studio. |
| Ship Lag (days) | int | Number of days between `Order Date` and `Ship Date`. Represents order fulfillment/processing time, not delivery time. Range: 0–7. |
| Profit Margin % | float | Row-level profit margin: `(Profit / Sales) × 100`, rounded to 2 decimal places. |
| Is Loss | bool | `True` if `Profit < 0`, `False` otherwise. 18.7% of rows are `True`. |
| Discount Tier | string | Discount bucketed into four levels: `None` (0%), `Low` (1–20%), `Medium` (21–40%), `High` (>40%). |
