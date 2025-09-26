# SQL--Grocery-Store-Management
Grocery Store Management (GSM) Database
📌 Project Overview

The Grocery Store Management (GSM) project is a relational database system designed to manage suppliers, products, customers, employees, and sales orders for a grocery store. It allows tracking of inventory, suppliers, orders, employees’ performance, and customer purchases.

This project demonstrates SQL database design, schema creation, queries, and analysis to derive business insights.

📂 Database Schema

The database contains the following tables:

Supplier – Stores supplier details.

Categories – Holds product categories.

Employees – Employees handling orders.

Customers – Customer details.

Products – Grocery products with supplier and category references.

Orders – Customer orders processed by employees.

Order Details – Line items of each order with quantity and price.



ER Diagram 

<img width="2575" height="1361" alt="image" src="https://github.com/user-attachments/assets/e2ab5616-92af-4f46-b7e4-95cc2e5fa91c" />



🛠️ Features & Queries

✅ Create and manage suppliers, categories, products, employees, and customers.

✅ Place orders linked with customers and employees.

✅ Track sales revenue, average order value, and supplier contributions.

✅ Analyze order patterns by weekday vs weekend.

✅ Identify top employees, top suppliers, and popular products.

🔍 Example SQL Queries
1. Total number of suppliers
SELECT COUNT(*) AS total_suppliers FROM supplier;

2. Supplier contributing the most products
SELECT s.sup_name, COUNT(p.prod_id) AS total_products
FROM supplier s
JOIN products p ON s.sup_id = p.sup_id
GROUP BY s.sup_name
ORDER BY total_products DESC
LIMIT 1;

3. Weekday vs Weekend Sales
SELECT 
    CASE WHEN DAYOFWEEK(order_date) IN (1,7) THEN 'Weekend' ELSE 'Weekday' END AS day_type,
    COUNT(DISTINCT o.ord_id) AS total_orders,
    SUM(od.quantity * od.each_price) AS total_sales
FROM orders o
JOIN order_details od ON o.ord_id = od.ord_id
GROUP BY day_type;

4. Top Employee by Total Sales
SELECT e.emp_name, SUM(od.quantity * od.each_price) AS total_sales
FROM employees e
JOIN orders o ON e.emp_id = o.emp_id
JOIN order_details od ON o.ord_id = od.ord_id
GROUP BY e.emp_name
ORDER BY total_sales DESC
LIMIT 1;

📊 Insights You Can Derive

🛒 Which products are ordered most frequently.

📦 Which suppliers contribute the most to sales.

👩‍💼 Which employees process the highest revenue.

📅 Whether weekend sales outperform weekday sales.

💰 Average order values per employee and per product.

🚀 How to Use

Clone this repository:

git clone https://github.com/your-username/grocery-store-management.git


Import the SQL script into MySQL:

source GSM.sql;


Run the queries provided in the queries.sql file to generate insights.

📌 Tech Stack

Database: MySQL

Queries: SQL (DDL, DML, Joins, Aggregations)

👤 Author

N. lokeswarreddy 

Data Analytics Enthusiast | SQL | Python | Power BI
