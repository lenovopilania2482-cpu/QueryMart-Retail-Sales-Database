# QueryMart – Retail Sales Database

## 📌 Project Overview

**QueryMart – Retail Sales Database** is a SQL-based retail data analysis project designed to explore and analyze customer, product, warehouse, order, and order-item data.

The project uses a **SQLite database** and Python to execute SQL queries and analyze retail sales information. It demonstrates practical SQL skills including data exploration, filtering, aggregation, grouping, sorting, and business-oriented analysis.

The project is implemented in a **Google Colab/Jupyter Notebook** using Python, SQLite, Pandas, and SQL queries.

---

## 🎯 Project Objectives

The main objectives of this project are:

- Explore the structure of a retail sales database.
- Understand customer and product information.
- Analyze orders and order items.
- Calculate total and average revenue.
- Identify different payment methods and order statuses.
- Analyze products by category and price.
- Find the most expensive products.
- Filter orders based on dates and delivery status.
- Practice SQL queries on a realistic retail database.

---

## 🗄️ Database Structure

The QueryMart database contains five main tables:

| Table | Description |
|---|---|
| `customers` | Contains customer information and customer segments |
| `products` | Contains product names, categories, and prices |
| `warehouses` | Contains warehouse-related information |
| `orders` | Contains customer orders, dates, payment methods, and order statuses |
| `order_items` | Contains individual items included in orders and their net amounts |

The notebook queries the SQLite database to identify these five tables.

### Customers

The customer table contains:

- `customer_id`
- `customer_name`
- `city`
- `age`
- `gender`
- `customer_segment`

The dataset contains **1,000 customer records**.

Customer segments include categories such as:

- Regular
- Premium
- VIP

---

### Products

The product table contains:

- `product_id`
- `product_name`
- `category`
- `unit_price`

The dataset contains products across categories including:

- Electronics
- Home
- Fashion
- Beauty
- Grocery

Examples include laptops, smartphones, tablets, smart watches, clothing, beauty products, and grocery items.

---

## 🛠️ Technologies Used

- **Python**
- **SQL**
- **SQLite**
- **Pandas**
- **Requests**
- **Google Colab / Jupyter Notebook**

The notebook imports `sqlite3`, `requests`, and `pandas` for database connectivity, downloading the database, and data analysis.

---

## 🔄 Project Workflow

### 1. Import Required Libraries

The project starts by importing the required Python libraries:

```python
import sqlite3
import requests
import pandas as pd
```

### 2. Download the Database

The SQLite database is downloaded and connected using Python:

```python
conn = sqlite3.connect("QueryMart.db")
```

A helper function is then created to execute SQL queries through Pandas:

```python
def sql(query):
    return pd.read_sql(query, conn)
```



### 3. Explore Database Tables

The project first identifies all tables available in the database:

```sql
SELECT name
FROM sqlite_master
WHERE type='table';
```

This returns:

```text
customers
products
warehouses
orders
order_items
```

---

## 📊 SQL Analysis Performed

The notebook demonstrates several practical SQL operations.

### Revenue Analysis

Total revenue is calculated from the `order_items` table:

```sql
SELECT SUM(net_amount)
FROM order_items;
```

Average order-item revenue is also calculated:

```sql
SELECT AVG(net_amount)
FROM order_items;
```

### Payment Method Analysis

Unique payment methods are identified using:

```sql
SELECT DISTINCT payment_method
FROM orders;
```

### Order Status Analysis

Unique order statuses are identified using:

```sql
SELECT DISTINCT order_status
FROM orders;
```

### Delivered Orders

The project filters delivered orders:

```sql
SELECT *
FROM orders
WHERE order_status = 'Delivered';
```

### Date-Based Order Analysis

Orders placed after June 2025 are identified using:

```sql
SELECT *
FROM orders
WHERE order_date >= '2025-07-01';
```

Orders placed between January and March 2025 are identified using:

```sql
SELECT *
FROM orders
WHERE order_date BETWEEN '2025-01-01' AND '2025-03-31';
```

---

## 🛍️ Product Analysis

The project also performs product-focused analysis.

### Total Number of Products

```sql
SELECT COUNT(*) AS total_products
FROM products;
```

### Products by Category

```sql
SELECT category, COUNT(*) AS num_products
FROM products
GROUP BY category;
```

### Most Expensive Products

The five most expensive products can be identified with:

```sql
SELECT product_id, product_name, unit_price
FROM products
ORDER BY unit_price DESC
LIMIT 5;
```

### Premium Products

Products priced above ₹10,000 are identified using:

```sql
SELECT product_id, product_name, category, unit_price
FROM products
WHERE unit_price > 10000;
```

---

## 📈 Key SQL Concepts Demonstrated

This project provides hands-on practice with:

- `SELECT`
- `WHERE`
- `DISTINCT`
- `COUNT()`
- `SUM()`
- `AVG()`
- `GROUP BY`
- `ORDER BY`
- `LIMIT`
- `BETWEEN`
- Date filtering
- SQLite database connections
- Pandas SQL integration

---

## 💡 Business Questions Explored

The project uses SQL to answer practical retail questions such as:

1. How much total revenue was generated?
2. What is the average order-item revenue?
3. What payment methods are used?
4. What order statuses exist?
5. Which orders have been delivered?
6. Which orders were placed during specific periods?
7. How many products are available?
8. How many products belong to each category?
9. Which products are the most expensive?
10. Which products are priced above ₹10,000?

---

## 📂 Project Structure

```text
QueryMart-Retail-Sales-Database/
│
├── QueryMart-Retail-Sales-Database.ipynb
└── README.md
```

The main notebook contains the complete Python and SQL analysis workflow.

---

## 🚀 How to Run the Project

### Option 1 – Google Colab

1. Open the `.ipynb` file in Google Colab.
2. Run the cells from top to bottom.
3. The notebook downloads the QueryMart SQLite database.
4. The database connection is created automatically.
5. Execute the SQL analysis cells to reproduce the results.

### Option 2 – Jupyter Notebook

Install the required Python packages:

```bash
pip install pandas requests
```

Then open:

```text
QueryMart-Retail-Sales-Database.ipynb
```

and execute the notebook cells.

---

## 📌 Project Outcome

This project demonstrates how a retail database can be explored using **SQL and Python** to extract meaningful information from customers, products, orders, and order items.

It is particularly useful as a **SQL portfolio project** for demonstrating database querying, retail analytics, data exploration, and practical business-question solving.

---

## 👩‍💻 Skills Demonstrated

**SQL | SQLite | Python | Pandas | Data Analysis | Database Querying | Retail Analytics | Data Exploration**

---

## 📄 Project File

The complete analysis is available in:

`QueryMart-Retail-Sales-Database.ipynb`