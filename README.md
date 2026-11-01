# Customer Shopping Behavior Analysis

An end-to-end data analytics project that explores 3,900 retail transactions to understand spending patterns, customer segments, product preferences, and subscription behavior.

**Tools:** Python (pandas, SQLAlchemy, pyodbc) · SQL Server (T-SQL) · Power BI (DAX)

![Dashboard](images/dashboard.png)

## Project Workflow
1. **Data cleaning and EDA (Python):** inspected the data with `info()` and `describe()`, imputed 37 missing review ratings using the median rating per product category, standardized column names to snake_case, and dropped a redundant column (`promo_code_used`).
2. **Feature engineering:** created `age_group` and `purchase_frequency_days`.
3. **Database integration:** loaded the cleaned DataFrame into SQL Server using SQLAlchemy and pyodbc.
4. **SQL analysis:** answered 10 business questions using aggregations, subqueries, CTEs, `CASE` logic, and window functions (`ROW_NUMBER`).
5. **Dashboard (Power BI):** built an interactive dashboard with DAX measures, slicers, and KPI cards.

## Dataset
- 3,900 rows, 18 columns
- Fields cover demographics (age, gender, location, subscription status), purchase details (item, category, amount, season, size, color), and shopping behavior (discounts, previous purchases, purchase frequency, review rating, shipping type)
- Source: *[add dataset link]*

## Business Questions Answered (SQL)
1. Revenue by gender
2. Discount users who still spent above average
3. Top 5 products by average review rating
4. Average spend: Standard vs Express shipping
5. Subscribers vs non-subscribers (average spend and total revenue)
6. Top 5 products by discount rate
7. Customer segmentation: New / Returning / Loyal
8. Top 3 products in each category
9. Are repeat buyers more likely to subscribe?
10. Revenue contribution by age group

## Key Findings
- **Total revenue is about $233K.** Male customers generate roughly 68% ($157,890) and female customers 32% ($75,191).
- **Subscribers do not spend more.** Average spend is $59.49 for subscribers vs $59.87 for non-subscribers, and only 27% of customers are subscribed.
- **Repeat buyers are not more likely to subscribe.** About 28% of repeat buyers (more than 5 previous purchases) subscribe, close to the overall rate.
- **About 80% of customers are "Loyal"** (3,116 of 3,900), so the business has a strong repeat base but few new customers (83).
- **Revenue is spread fairly evenly across age groups.** Young Adults lead ($62,143) and Seniors are lowest ($55,763).
- **Express shipping customers spend slightly more** ($60.48 vs $58.46 for Standard).
- **Discount dependence is high:** Hat, Sneakers, Coat, Sweater and Pants each have 47-50% of purchases discounted.
- **Product ratings are tightly clustered** (3.78 to 3.86 for the top 5), so ratings alone do not separate products much.

## Recommendations
- **Rework the subscription offer.** Subscribers show no extra spend, so add real member benefits before pushing more sign-ups.
- **Review discount policy,** especially on the five most-discounted products, to protect margin.
- **Grow the new-customer pipeline,** since the base is overwhelmingly existing customers.
- **Feature best-selling and top-rated products** in campaigns.
- **Test express-shipping promotions** for higher-spending segments.

## How to Run
1. Clone the repo and install dependencies: `pip install pandas sqlalchemy pyodbc`
2. Install [ODBC Driver 18 for SQL Server](https://learn.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) and create a database: `CREATE DATABASE customer_behavior;`
3. Run the notebook `customer_behavior_analysis.ipynb` to clean the data and load the `customer` table.
4. Run `sql/analysis_queries.sql` in SQL Server Management Studio.
5. Open `dashboard/customer_behavior.pbix` in Power BI Desktop and point it to your SQL Server instance.

## Repository Structure
```
├── data/                  # raw dataset
├── notebooks/             # Python cleaning and EDA
├── sql/                   # T-SQL analysis queries
├── dashboard/             # Power BI file (.pbix)
├── images/                # dashboard screenshot
└── README.md
```

## Author
**Siddhi Ambre** · [LinkedIn](https://linkedin.com/in/siddhiambre-915bb627a)
