# 🛍️ Retail Sales SQL Project

This project demonstrates SQL-based data cleaning, exploration, and analysis using a retail sales dataset. It simulates a real-world scenario where raw transactional data is analyzed to extract actionable business insights.

## 📁 Project Overview

**File:** `retail sales.sql`  
**Database Name:** `sql_project_p2`  
**Table:** `retail_sales`

The project includes:
- Table creation and initial setup
- Data quality checks and cleaning
- Exploratory data analysis
- Business questions and insights using SQL queries

---

## 🧱 Table Structure

The `retail_sales` table includes the following fields:

- `transactions_id` (INT, Primary Key)
- `sale_date` (DATE)
- `sale_time` (TIME)
- `customer_id` (INT)
- `gender` (VARCHAR)
- `age` (INT)
- `category` (VARCHAR)
- `quantiy` (INT)
- `price_per_unit` (FLOAT)
- `cogs` (FLOAT)
- `total_sale` (FLOAT)

---

## 🧹 Data Cleaning

The script includes checks and deletions of rows with `NULL` values in critical fields like:
- `transactions_id`
- `sale_date`
- `sale_time`
- `gender`
- `category`
- `quantiy`
- `cogs`
- `total_sale`

---

## 📊 Data Analysis

### 🔍 Business Questions and SQL Solutions

**Q1. Retrieve all columns for sales made on '2022-11-05':**
```sql
SELECT * FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Q2. Retrieve all transactions where the category is 'Clothing' and quantity sold is more than 4 in November 2022:**
```sql
SELECT * FROM retail_sales
WHERE category = 'Clothing'
  AND TO_CHAR(sale_date, 'YYYY-MM') = '2022-11'
  AND quantiy >= 4;
```

**Q3. Calculate the total sales for each category:**
```sql
SELECT category, SUM(total_sale) as net_sale, COUNT(*) as total_orders
FROM retail_sales
GROUP BY category;
```

**Q4. Find the average age of customers who purchased items from the 'Beauty' category:**
```sql
SELECT ROUND(AVG(age), 2) as avg_age
FROM retail_sales
WHERE category = 'Beauty';
```

**Q5. Find all transactions where total sale is greater than 1000:**
```sql
SELECT * FROM retail_sales
WHERE total_sale > 1000;
```

**Q6. Find the total number of transactions by each gender in each category:**
```sql
SELECT category, gender, COUNT(*) as total_trans
FROM retail_sales
GROUP BY category, gender
ORDER BY category;
```

**Q7. Calculate the average sale for each month and find the best-selling month per year:**
```sql
SELECT year, month, AVG_sale
FROM (
    SELECT EXTRACT(YEAR FROM sale_date) as year,
           EXTRACT(MONTH FROM sale_date) as month,
           AVG(total_sale) as avg_sale,
           RANK() OVER (PARTITION BY EXTRACT(YEAR FROM sale_date) ORDER BY AVG(total_sale) DESC) as rank
    FROM retail_sales
    GROUP BY year, month
) as t1
WHERE rank = 1;
```

**Q8. Find the top 5 customers based on total sales:**
```sql
SELECT customer_id, SUM(total_sale) as total_sales
FROM retail_sales
GROUP BY customer_id
ORDER BY total_sales DESC
LIMIT 5;
```

**Q9. Find the number of unique customers who purchased from each category:**
```sql
SELECT category, COUNT(DISTINCT customer_id) as cnt_unique_cs
FROM retail_sales
GROUP BY category;
```

**Q10. Classify each sale into shifts and count number of orders per shift (Morning <12, Afternoon 12–17, Evening >17):**
```sql
WITH hourly_sale AS (
    SELECT *,
           CASE 
               WHEN EXTRACT(HOUR FROM sale_time) < 12 THEN 'Morning'
               WHEN EXTRACT(HOUR FROM sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
               ELSE 'Evening'
           END AS shift 
    FROM retail_sales
)
SELECT shift, COUNT(*) as total_orders
FROM hourly_sale
GROUP BY shift;
```

---

## 💡 Tools Used

- PostgreSQL (or any SQL-compatible RDBMS)
- SQL queries for data manipulation and analysis

---

## 🎯 Objective

The objective of this project is to showcase end-to-end SQL skills including:
- Data cleaning
- Query writing
- Aggregation and grouping
- Time-based and categorical analysis
- Business insights generation

---

## 📌 Key Learnings

- Importance of data preprocessing before analysis
- Query optimization using filters and window functions
- Grouped analysis to uncover customer and sales behavior
- Real-world shift mapping using `CASE` statements

---

## ✅ How to Run

1. Import the SQL file into your preferred SQL environment.
2. Execute each block of SQL code step-by-step.
3. Review the results and insights for each analysis question.

---

## 📬 Contact

For feedback or collaboration, feel free to connect with me on [LinkedIn](https://www.linkedin.com/in/chandan-shakya-0580a0209/)
