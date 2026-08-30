# Food Delivery Orders — Data Analysis

Exploratory data analysis and business reporting project on a 50,000-row food delivery orders dataset, covering data cleaning in Python, deep-dive column analysis in Excel, and a written business report of findings. Built as a solo project to practice end-to-end analysis: from raw data to actionable, quantified insights.

## Project Workflow

1. **Data acquisition** — Raw dataset (`food_delivery_orders_dataset.csv`, 50,000 rows × 37 columns) sourced from Kaggle.
2. **Cleaning & EDA in Python** (`Data_analysis.ipynb`) — Inspected structure, checked for duplicates, diagnosed and handled missing values, fixed data types, and exported a cleaned copy.
3. **Deep-dive analysis in Excel** (`new_food_delivery_orders_cleaned_.xlsx`) — Cleaned data broken out into focused sheets (City, Category/Order Status, Delivery Details, Cancellation Reasons, Tips, Time Analysis) for column-by-column exploration.
4. **Business reporting** (`Data_Analysis_Report.odt`) — Findings written up with quantified, city/category/time-level breakdowns.

## Key Skills Demonstrated

- **Python / Pandas** — data inspection, duplicate detection, null-value diagnosis and imputation strategy, datetime conversion
- **Data cleaning logic** — identifying *why* values are missing (e.g. cancelled orders have no delivery time or rating) rather than blindly imputing
- **Excel** — structured multi-sheet deep analysis
- **Business analysis & reporting** — translating cleaned data into concrete, quantified insights

## Data Cleaning Highlights

- Diagnosed that 49,132 of 50,000 missing `cancellation_reason` values meant "not cancelled," not missing data — confirmed by cross-checking against the 868 nulls in delivery time, lateness, and rating columns (49,132 + 868 = 50,000, the full dataset).
- Filled `cancellation_reason` with `"Not Cancelled"` and `tip_amount` with `0` for completed orders where relevant.
- Imputed `actual_delivery_time_minutes`, `late_delivery`, and `customer_rating` with the column mean for cancelled orders, to keep columns numeric for downstream Power BI use, while documenting that these values don't represent a real delivery outcome.
- Converted `order_date` and `order_timestamp` to proper datetime types for time-based analysis.

## Key Findings

- **98.3%** of orders (49,132 / 50,000) completed successfully; **1.7%** (868) were cancelled.
- **Driver Unassigned** is the single largest cancellation cause — 44.5% of all cancellations.
- **36.6%** of completed orders were delivered late; average actual delivery time (35.15 min) ran ~4.2 minutes over the estimate (30.92 min).
- **Storm weather** produced both the longest average delivery time (47.07 min) and the highest late-delivery rate (89.2%), versus 24.5% in clear weather.
- **City_A and City_B** together generated ~70.4% of completed order value; **Fast Food** was the top-performing restaurant type (~47.9% of completed order value).
- **Thursday** was the strongest day for order value across every city, with mid-week (Wed–Thu) demand notably higher than the rest of the week.
- Average customer rating: **4.30/5**; delivery partners rated highest on average at **4.50/5**.

## Files

| File | Description |
|---|---|
| `food_delivery_orders_dataset.csv` | Raw dataset from Kaggle |
| `Data_analysis.ipynb` | Cleaning & initial EDA notebook |
| `new_food_delivery_orders_cleaned.csv` | Cleaned dataset (CSV) |
| `new_food_delivery_orders_cleaned_.xlsx` | Cleaned dataset with sheet-by-sheet deep analysis |
| `Data_Analysis_Report.odt` | Written business report of findings |

## Next Steps

- Connect the cleaned dataset to Power BI for an interactive, auto-refreshing dashboard (in progress).
- Move the cleaned data into a proper database (SQLite/PostgreSQL) so Power BI/Excel can query it live instead of a static file.
