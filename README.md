# 📊 SQL Customer Order Analysis

## 📌 Project Overview

**SQL Project** is a database project that manages customer order information using SQL. It stores order IDs, customer IDs, order amounts, and order dates. The project uses **SQL window functions** such as `SUM() OVER()` to calculate customer-wise running totals, overall running totals, and daily sales running totals.

## 🎯 Objectives

* Manage customer order data using SQL.
* Calculate customer-wise running totals.
* Calculate overall running sales totals.
* Analyze daily sales and cumulative sales.
* Practice SQL window functions and Common Table Expressions (CTEs).

## 🗃️ Database Structure

The project contains the following fields:

| Column       | Description                    |
| ------------ | ------------------------------ |
| `ORDERID`    | Unique order ID                |
| `CUSTOMERID` | Customer identification number |
| `AMOUNT`     | Order amount                   |
| `ORDER_DATE` | Date of the order              |

## 🔍 SQL Concepts Used

* `CREATE TABLE`
* `INSERT INTO`
* `SELECT`
* `SUM()`
* `GROUP BY`
* `OVER()`
* `PARTITION BY`
* `ORDER BY`
* `WITH` / CTE
* Running Total

## 📈 Analysis Performed

### 1. Customer Running Total

Calculates the cumulative order amount for each customer based on the order date.

```sql
SUM(AMOUNT) OVER(
    PARTITION BY CUSTOMERID
    ORDER BY ORDER_DATE
) AS CustomerRunningTotal
```

### 2. Overall Running Total

Calculates the cumulative amount across all orders based on order date and order ID.

```sql
SUM(AMOUNT) OVER(
    ORDER BY ORDER_DATE, ORDERID
) AS RunningTotal
```

### 3. Daily Sales Running Total

First calculates total sales for each day and then calculates the cumulative daily sales.

```sql
WITH DailySales AS (
    SELECT ORDER_DATE, SUM(AMOUNT) AS DailyAmount
    FROM EEMPLOYY
    GROUP BY ORDER_DATE
)
SELECT
    ORDER_DATE,
    DailyAmount,
    SUM(DailyAmount) OVER(ORDER BY ORDER_DATE) AS RunningTotal
FROM DailySales;
```

## 🛠️ Technologies Used

* SQL
* MySQL
* Window Functions
* Common Table Expressions (CTE)

## 📂 Project Structure

```text
SQL-Project/
│
├── README.md
└── sql_project.sql
```

## 🚀 How to Run

1. Open MySQL Workbench or any MySQL-compatible SQL environment.
2. Create the required table.
3. Insert the sample order data.
4. Run the SQL queries.
5. View the customer-wise and daily running totals.

## 📚 Learning Outcome

This project demonstrates practical use of **SQL window functions, running totals, grouping, ordering, and CTEs** for analyzing customer order and sales data.
.
