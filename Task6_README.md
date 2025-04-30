
# Task 6: Sales Trend Analysis Using Aggregations

## Objective
Analyze monthly revenue and order volume using SQL aggregate functions in PostgreSQL. This task demonstrates how to group and aggregate time-series data to extract meaningful business insights.

---

## Tools Used
- PostgreSQL 17
- pgAdmin 4
- Google Sheets (for chart)
- GitHub

---

## Dataset
A simulated `orders` table was created with the following columns:
- `order_id`: Unique order identifier
- `order_date`: Date of order
- `amount`: Order value
- `product_id`: ID of the product sold

---

## SQL Queries Used

### 1. Monthly Revenue and Order Volume
```sql
SELECT
  EXTRACT(YEAR FROM order_date) AS order_year,
  EXTRACT(MONTH FROM order_date) AS order_month,
  TO_CHAR(order_date, 'Month') AS month_name,
  SUM(amount) AS monthly_revenue,
  COUNT(DISTINCT order_id) AS order_volume
FROM
  orders
GROUP BY
  EXTRACT(YEAR FROM order_date),
  EXTRACT(MONTH FROM order_date),
  TO_CHAR(order_date, 'Month')
ORDER BY
  order_year,
  order_month;
```

### 2. Product-wise Total Sales
```sql
SELECT
  product_id,
  SUM(amount) AS total_sales
FROM
  orders
GROUP BY
  product_id
ORDER BY
  total_sales DESC;
```

---

## Exported Results
- `monthly_sales_analysis.csv`: Exported from pgAdmin
- `result.png`: Screenshot of SQL output
- `sales_chart.png`: Visualization of monthly revenue
- `product_sales_chart.png`: Visualization of total sales by product

---

## Visualizations

### Monthly Revenue
![sales_chart]("Monthly Revenue .png")

This bar chart shows monthly sales trends. March 2023 had the highest revenue, indicating a strong Q1 sales period.

## Conclusion
- March saw the highest monthly revenue and order count.
- Product analysis shows which products generate the most income.
- The project demonstrates how SQL can uncover trends and performance patterns through aggregations and grouping.

---

## What I Learned
I learned to:
- Group data by time using `EXTRACT()` and `TO_CHAR()`
- Use `SUM()` and `COUNT()` to measure key metrics
- Build visualizations for storytelling
- Structure data analysis results for portfolio use

---

