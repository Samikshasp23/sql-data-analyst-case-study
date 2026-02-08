# SQL Project – Real-Life Data Analyst Case Study

## 📌 Project Overview
This project is a **real-life SQL case study** designed to demonstrate practical data analysis skills using relational databases.  
The analysis focuses on **user behavior, product sales, and revenue generation**, including identifying revenue from **Gold users**.

The project simulates real-world data challenges such as **dirty data**, **data type mismatches**, and **data cleansing**, which are commonly faced by data analysts.

---

## 🗂️ Dataset Description

The project consists of the following tables:

### 1️⃣ `sales`
Contains transaction-level sales data.

| Column Name   | Data Type |
|--------------|----------|
| userid       | INT / VARCHAR |
| created_date | DATE |
| product_id   | INT / VARCHAR |

---

### 2️⃣ `product`
Stores product master information.

| Column Name   | Data Type |
|--------------|----------|
| product_id   | INT |
| product_name | VARCHAR |
| price        | INT |

---

### 3️⃣ `User_Names`
Maps user IDs to user names.

| Column Name | Data Type |
|------------|----------|
| userid     | INT |
| names      | VARCHAR |

---

### 4️⃣ `Golduser_Signup`
Tracks users who signed up for Gold membership.

| Column Name | Data Type |
|------------|----------|
| userid     | INT / VARCHAR |
| signup_date | DATE / VARCHAR |

---

## ⚠️ Data Quality Challenges
Some tables contain **invalid placeholder values (`'*'`)** in numeric columns.  
This reflects real-world scenarios where data ingestion pipelines may introduce inconsistencies.

### Example Issues:
- `userid = '*'`
- `product_id = '*'`
- `signup_date = '*'`

These issues were handled using:
- Data cleansing (`DELETE`)
- Defensive SQL (`TRY_CAST()`)

---

## 🧹 Data Cleaning Queries

```sql
DELETE FROM sales
WHERE userid = '*' OR product_id = '*';

DELETE FROM Golduser_Signup
WHERE userid = '*' OR signup_date = '*';
