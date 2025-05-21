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

The SQL file answers 10 key business questions using SQL queries, including:

1. Sales on a specific date
2. High-volume clothing transactions in November 2022
3. Total sales per category
4. Average age of customers in the Beauty category
5. Transactions with total sale > 1000
6. Transaction count by gender and category
7. Average monthly sales and best-selling month per year
8. Top 5 customers by total sales
9. Unique customers per category
10. Sales shift analysis (Morning, Afternoon, Evening)

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
