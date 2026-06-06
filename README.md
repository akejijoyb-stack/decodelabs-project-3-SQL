# decodelabs-project-3-SQL
# SQL Data Analysis Project

## Project Overview

This project focuses on analyzing an e-commerce dataset using Microsoft SQL Server. The objective was to extract meaningful business insights by querying transactional data, applying filters, grouping records, and performing aggregations.

The analysis was conducted on a cleaned dataset containing customer orders, products, payment methods, referral sources, and order statuses.

---

## Objectives

* Retrieve data using SELECT statements
* Filter records using WHERE clauses
* Sort results using ORDER BY
* Group data using GROUP BY
* Perform aggregations using COUNT(), SUM(), and AVG()
* Generate business insights from transactional data

---

## Tools Used

* Microsoft SQL Server
* SQL Server Management Studio (SSMS)

---

## Dataset Summary

| Metric              | Value         |
| ------------------- | ------------- |
| Total Records       | 1,200         |
| Total Revenue       | $1,264,761.96 |
| Average Order Value | $1,053.97     |

---

# Query 1: Total Number of Orders

### SQL Query

```sql
SELECT COUNT(*) AS Total_Orders
FROM [Cleaned Data];
```

### Result

1,200 Orders

### Insight

The dataset contains 1,200 customer transactions available for analysis.

### Screenshot

<img width="1365" height="698" alt="Screenshot 2026-06-05 182803" src="https://github.com/user-attachments/assets/87207945-6999-4d5c-af43-115b0354aede" />

---

# Query 2: Total Revenue

### SQL Query

```sql
SELECT SUM([Total Price]) AS Total_Revenue
FROM [Cleaned Data];
```

### Result

$1,264,761.96

### Insight

The business generated over $1.26 million in revenue from customer transactions.

### Screenshot

<img width="1365" height="698" alt="Screenshot 2026-06-05 182803" src="https://github.com/user-attachments/assets/3e6dcab5-6d48-4548-a1fd-14be3bf63c9b" />


---

# Query 3: Average Order Value

### SQL Query

```sql
SELECT AVG([Total Price]) AS Average_Order_Value
FROM [Cleaned Data];
```

### Result

$1,053.97

### Insight

Customers spend an average of approximately $1,054 per order.

---

# Query 4: Revenue by Product

### SQL Query

```sql
SELECT Product,
       SUM([Total Price]) AS Revenue
FROM [Cleaned Data]
GROUP BY Product
ORDER BY Revenue DESC;
```

### Insight

Chair generated the highest revenue, followed closely by Printer and Laptop. These products contribute significantly to overall sales performance.

---

# Query 5: Revenue by Referral Source

### SQL Query

```sql
SELECT [Referral Source],
       SUM([Total Price]) AS Revenue
FROM [Cleaned Data]
GROUP BY [Referral Source]
ORDER BY Revenue DESC;
```

### Results

| Referral Source | Revenue     |
| --------------- | ----------- |
| Instagram       | $275,285.45 |
| Email           | $261,808.55 |
| Google          | $250,441.48 |
| Facebook        | $250,410.90 |
| Referral        | $226,815.58 |

### Insight

Instagram generated the highest revenue, making it the most effective customer acquisition channel.

---

# Query 6: Orders by Payment Method

### SQL Query

SELECT [Payment Method],
       COUNT(*) AS NumberOfOrders
FROM [Cleaned Data]
GROUP BY [Payment Method]
ORDER BY NumberOfOrders DESC;
```

### Insight

Online payments were the most frequently used payment method, indicating a strong customer preference for digital transactions.

---

# Query 7: Order Status Distribution

### SQL Query

SELECT [Order Status],
       COUNT(*) AS TotalOrders
FROM [Cleaned Data]
GROUP BY [Order Status]
ORDER BY TotalOrders DESC;
```

### Insight

Cancelled orders represented the largest order-status category, suggesting an opportunity to improve order fulfillment and customer satisfaction.

---

# Query 8: Most Popular Products by Quantity Sold

### SQL Query

SELECT Product,
       SUM(Quantity) AS QuantitySold
FROM [Cleaned Data]
GROUP BY Product
ORDER BY QuantitySold DESC;
```

### Insight

Chair was the most purchased product based on quantity sold, demonstrating strong customer demand.

---

# Query 9: High-Value Orders

### SQL Query

SELECT *
FROM [Cleaned Data]
WHERE [Total Price] >
(
    SELECT AVG([Total Price])
    FROM [Cleaned Data]
);
```

### Insight

This query filters orders whose Total Price exceeds the overall average order value ($1,053.97). These transactions represent high-value purchases and can help identify premium customers and top-performing sales.

---

# Query 10: Top 10 Highest-Value Orders

### SQL Query

SELECT TOP 10
       [Order ID],
       Product,
       [Total Price]
FROM [Cleaned Data]
ORDER BY [Total Price] DESC;
```

### Insight

This query highlights the highest-value transactions and the products associated with them, helping identify top revenue-generating sales.
<img width="1365" height="730" alt="SQL1" src="https://github.com/user-attachments/assets/8cde3853-46fd-4d5c-a292-fe45c86aa34d" />

---

# Key Findings

* The business generated a total revenue of $1,264,761.96.
* The average order value was $1,053.97.
* Chair was the highest revenue-generating product.
* Instagram was the most effective referral source by revenue.
* Online payments were the most commonly used payment method.
* Cancelled orders represented the largest order-status category.
* High-value transactions provide opportunities for customer segmentation and targeted marketing.

---

# Skills Demonstrated

* SQL Querying
* Data Filtering
* Data Aggregation
* Data Grouping
* Business Insight Generation
* Data Analysis using Microsoft SQL Server

---

## Files Included
- Cleaned Dataset1.csv
- SQL Queries.sql
- README.md
