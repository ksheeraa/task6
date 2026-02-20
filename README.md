# Online Sales Data Analysis Project

This project involves setting up a relational database for online sales records and performing various data analysis tasks using SQLite. The dataset includes information on transactions, products, revenue, and customer regions.

## 📊 Project Overview
The goal of this project was to transform raw sales data into actionable insights, such as identifying top-performing products, regional sales distribution, and monthly revenue trends.

## 🛠️ Database Schema
The database consists of a single table named `OnlineSalesData` with the following structure:

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `transaction_id` | INTEGER | Unique identifier for each sale |
| `date` | TEXT | Date of transaction (YYYY-MM-DD) |
| `product_category`| TEXT | Category of the product (Electronics, Clothing, etc.) |
| `product_name` | TEXT | Specific name of the product |
| `units_sold` | INTEGER | Number of items purchased |
| `unit_price` | REAL | Price per single unit |
| `total_revenue` | REAL | Total sale amount (Units Sold * Unit Price) |
| `region` | TEXT | Geographic location of the sale |
| `payment_method` | TEXT | Method used for payment |

## 🚀 Work Done

### 1. Data Cleaning & Preparation
* **Table Structuring:** Created a structured SQLite table with optimized data types (`REAL` for prices, `INTEGER` for counts) to replace initial generic text-only columns.
* **Data Migration:** Imported records from the `Online Sales Data.csv` into the SQLite environment.

### 2. Business Logic Implementation
Developed and executed a suite of SQL queries to answer critical business questions:
* **Revenue Analysis:** Calculated total revenue per product category, identifying **Electronics** and **Home Appliances** as high-value drivers.
* **Regional Performance:** Aggregated transaction counts to see which global regions (North America, Asia, Europe) generate the most volume.
* **Product Performance:** Identified the Top 5 products by revenue, including high-ticket items like the **iPhone 14 Pro** and **MacBook Pro**.
* **Operational Metrics:** Analyzed average unit prices and average units per transaction to understand customer buying patterns.

### 3. Temporal Trends
* Utilized the `strftime` function to extract months from date strings, allowing for the calculation of total revenue for each month to observe seasonal trends.

## 🔍 Key Queries Used

### Top 5 Products by Revenue
```sql
SELECT product_name, SUM(total_revenue) AS revenue
FROM OnlineSalesData
GROUP BY product_name
ORDER BY revenue DESC
LIMIT 5;
