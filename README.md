# 🛒 Retail Sales Analysis using SQL

This project demonstrates fundamental SQL skills used by data analysts to clean, explore, and analyze retail sales data. The project covers database creation, data cleaning, exploratory data analysis (EDA), and solving real-world business questions using SQL.


**Skills Used**
- SQL
- Data Cleaning
- Exploratory Data Analysis (EDA)
- Aggregate Functions
- GROUP BY
- CASE Statements
- Date Functions
- Window Functions (if used)

Database: PostgreSQL

## 📂 Dataset

The dataset contains retail transaction records with:

-   Transaction ID
-   Sale Date & Time
-   Customer ID
-   Gender
-   Age
-   Product Category
-   Quantity
-   Price per Unit
-   Cost of Goods Sold (COGS)
-   Total Sale
  
---

# 📌 Project Overview

**Project Title**: Retail Sales Analysis  
**Database**: `retail_sales_SQL_project`

This project is designed to demonstrate SQL skills and techniques typically used by data analysts to explore, clean, and analyze retail sales data. The project involves setting up a retail sales database, performing exploratory data analysis (EDA), and answering specific business questions through SQL queries. This project is ideal for those who are starting their journey in data analysis and want to build a solid foundation in SQL.

---

# Objectives

1. **Set up a retail sales database**: Create and populate a retail sales database with the provided sales data.
2. **Data Cleaning**: Identify and remove any records with missing or null values.
3. **Exploratory Data Analysis (EDA)**: Perform basic exploratory data analysis to understand the dataset.
4. **Business Analysis**: Use SQL to answer specific business questions and derive insights from the sales data.

---

# Project Structure

# 📂 Database Setup

- **Database Creation**: The project starts by creating a database named `retail_sales_SQL_project`.
- **Table Creation**: A table named `retail_sales` is created to store the sales data. The table structure includes columns for transaction ID, sale date, sale time, customer ID, gender, age, product category, quantity sold, price per unit, cost of goods sold (COGS), and total sale amount.

```sql
CREATE DATABASE retail_sales_SQL_project;

CREATE TABLE retail_sales
(
    transactions_id INT PRIMARY KEY,
    sale_date DATE,	
    sale_time TIME,
    customer_id INT,	
    gender VARCHAR(10),
    age INT,
    category VARCHAR(35),
    quantity INT,
    price_per_unit FLOAT,	
    cogs FLOAT,
    total_sale FLOAT
);
```
---

#  Data Exploration & Cleaning

- **Record Count**: Determine the total number of records in the dataset.
- **Customer Count**: Find out how many unique customers are in the dataset.
- **Category Count**: Identify all unique product categories in the dataset.
- **Null Value Check**: Check for any null values in the dataset and delete records with missing data.

```sql
SELECT COUNT(*) FROM retail_sales;
SELECT COUNT(DISTINCT customer_id) FROM retail_sales;
SELECT DISTINCT category FROM retail_sales;

SELECT * FROM retail_sales
WHERE 
    sale_date IS NULL OR sale_time IS NULL OR customer_id IS NULL OR 
    gender IS NULL OR age IS NULL OR category IS NULL OR 
    quantity IS NULL OR price_per_unit IS NULL OR cogs IS NULL;

DELETE FROM retail_sales
WHERE 
    sale_date IS NULL OR sale_time IS NULL OR customer_id IS NULL OR 
    gender IS NULL OR age IS NULL OR category IS NULL OR 
    quantity IS NULL OR price_per_unit IS NULL OR cogs IS NULL;
```
---

# 📈 Business Questions Solved

The following SQL queries were developed to answer specific business questions:


### 1. Write a SQL query to retrieve all columns for sales made on '2022-11-05'.

**SQL Query**

```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Output**
| transactions_id | sale_date  | sale_time | customer_id | gender | age | category    | quantity | price_per_unit | cogs  | total_sale |
|-----------------|------------|-----------|-------------|--------|-----|-------------|----------|----------------|-------|------------|
| 180             | 2022-11-05 | 10:47:00  | 117         | Male   | 41  | Clothing    | 3        | 300.0          | 129.0 | 900.0      |
| 240             | 2022-11-05 | 11:49:00  | 95          | Female | 23  | Beauty      | 1        | 300.0          | 123.0 | 300.0      |
| 1256            | 2022-11-05 | 09:58:00  | 29          | Male   | 23  | Clothing    | 2        | 500.0          | 190.0 | 1000.0     |
| 1587            | 2022-11-05 | 20:06:00  | 140         | Female | 40  | Beauty      | 4        | 300.0          | 105.0 | 1200.0     |
| 1819            | 2022-11-05 | 20:44:00  | 83          | Female | 35  | Beauty      | 2        | 50.0           | 13.5  | 100.0      |
| 943             | 2022-11-05 | 19:29:00  | 90          | Female | 57  | Clothing    | 4        | 300.0          | 318.0 | 1200.0     |
| 1896            | 2022-11-05 | 20:19:00  | 87          | Female | 30  | Electronics | 2        | 25.0           | 30.75 | 50.0       |
| 1137            | 2022-11-05 | 22:34:00  | 104         | Male   | 46  | Beauty      | 2        | 500.0          | 145.0 | 1000.0     |
| 856             | 2022-11-05 | 17:43:00  | 102         | Male   | 54  | Electronics | 4        | 30.0           | 9.3   | 120.0      |
| 214             | 2022-11-05 | 16:31:00  | 53          | Male   | 20  | Beauty      | 2        | 30.0           | 8.1   | 60.0       |
| 1265            | 2022-11-05 | 14:35:00  | 86          | Male   | 55  | Clothing    | 3        | 300.0          | 111.0 | 900.0      |

---

### 2. Write a SQL query to retrieve all transactions where the category is 'Clothing', and the quantity sold is more than 4 in the month of Nov-2022.

   
**SQL Query**

```sql
SELECT 
	*
FROM retail_sales
WHERE 
	category = 'Clothing'
	AND 
	TO_CHAR(sale_date, 'YYYY-MM') = '2022-11'
	AND 
	quantity >=4;
```

**Output**

| transactions_id | sale_date  | sale_time | customer_id | gender | age | category | quantity | price_per_unit | cogs  | total_sale |
|-----------------|------------|-----------|-------------|--------|-----|----------|----------|----------------|-------|------------|
| 1484            | 2022-11-23 | 09:29:00  | 22          | Female | 19  | Clothing | 4        | 300.0          | 147.0 | 1200.0     |
| 64              | 2022-11-15 | 06:34:00  | 7           | Male   | 49  | Clothing | 4        | 25.0           | 8.5   | 100.0      |
| 284             | 2022-11-12 | 09:17:00  | 129         | Male   | 43  | Clothing | 4        | 50.0           | 20.5  | 200.0      |
| 1885            | 2022-11-09 | 07:32:00  | 148         | Female | 52  | Clothing | 4        | 30.0           | 10.8  | 120.0      |
| 547             | 2022-11-14 | 07:36:00  | 3           | Male   | 63  | Clothing | 4        | 500.0          | 250.0 | 2000.0     |
| 159             | 2022-11-10 | 21:30:00  | 42          | Male   | 26  | Clothing | 4        | 50.0           | 23.5  | 200.0      |
| 699             | 2022-11-21 | 22:21:00  | 129         | Female | 37  | Clothing | 4        | 30.0           | 16.2  | 120.0      |
| 1259            | 2022-11-03 | 17:31:00  | 105         | Female | 45  | Clothing | 4        | 50.0           | 21.0  | 200.0      |
| 146             | 2022-11-10 | 22:01:00  | 74          | Male   | 38  | Clothing | 4        | 50.0           | 49.0  | 200.0      |
| 1476            | 2022-11-11 | 22:27:00  | 130         | Female | 27  | Clothing | 4        | 500.0          | 555.0 | 2000.0     |
| 1296            | 2022-11-26 | 20:42:00  | 45          | Female | 22  | Clothing | 4        | 300.0          | 342.0 | 1200.0     |
| 1696            | 2022-11-21 | 17:59:00  | 24          | Female | 50  | Clothing | 4        | 50.0           | 55.0  | 200.0      |
| 1497            | 2022-11-19 | 21:44:00  | 109         | Male   | 41  | Clothing | 4        | 30.0           | 32.4  | 120.0      |
| 735             | 2022-11-26 | 21:38:00  | 153         | Female | 64  | Clothing | 4        | 500.0          | 515.0 | 2000.0     |
| 943             | 2022-11-05 | 19:29:00  | 90          | Female | 57  | Clothing | 4        | 300.0          | 318.0 | 1200.0     |
| 965             | 2022-11-27 | 21:45:00  | 84          | Male   | 22  | Clothing | 4        | 50.0           | 13.0  | 200.0      |
| 1615            | 2022-11-17 | 13:43:00  | 82          | Female | 61  | Clothing | 4        | 25.0           | 13.5  | 100.0      |

---

### 3. Write a SQL query to calculate the total sales (total_sale) for each category.

 
**SQL Query**

```sql
SELECT
	category,
	SUM(total_sale) AS net_sale,
	COUNT(*) AS total_orders
FROM retaiL_sales
GROUP BY 1;
```

**Output**

| category    | net_sale | total_orders |
|-------------|----------|--------------|
| Electronics | 313810.0 | 684          |
| Clothing    | 311070.0 | 701          |
| Beauty      | 286840.0 | 612          |

---

### 4. Write a SQL query to find the average age of customers who purchased items from the 'Beauty' category.

   
**SQL Query**

```sql
SELECT 
	ROUND(AVG(age), 2) AS avg_age
FROM retail_sales
WHERE category = 'Beauty';
```

**Output**

| avg_age |
|---------|
| 40.39   |

---

### 5. Write a SQL query to find all transactions where the total_sale is greater than 1000.

   
**SQL Query**

```sql
SELECT 	
	*
FROm retail_sales
WHERE total_sale > 1000;
```

**Output**
##(Limit to 50 due to size constraint)

| transactions_id | sale_date  | sale_time | customer_id | gender | age | category    | quantity | price_per_unit | cogs  | total_sale |
|-----------------|------------|-----------|-------------|--------|-----|-------------|----------|----------------|-------|------------|
| 522             | 2022-07-09 | 11:00:00  | 52          | Male   | 46  | Beauty      | 3        | 500.0          | 145.0 | 1500.0     |
| 559             | 2022-12-12 | 10:48:00  | 5           | Female | 40  | Clothing    | 4        | 300.0          | 84.0  | 1200.0     |
| 1522            | 2022-11-14 | 08:35:00  | 48          | Male   | 46  | Beauty      | 3        | 500.0          | 235.0 | 1500.0     |
| 1559            | 2022-08-20 | 07:40:00  | 49          | Female | 40  | Clothing    | 4        | 300.0          | 144.0 | 1200.0     |
| 421             | 2022-04-08 | 08:43:00  | 66          | Female | 37  | Clothing    | 3        | 500.0          | 235.0 | 1500.0     |
| 1421            | 2022-01-17 | 07:07:00  | 59          | Female | 37  | Clothing    | 3        | 500.0          | 185.0 | 1500.0     |
| 484             | 2022-03-13 | 07:52:00  | 135         | Female | 19  | Clothing    | 4        | 300.0          | 75.0  | 1200.0     |
| 1484            | 2022-11-23 | 09:29:00  | 22          | Female | 19  | Clothing    | 4        | 300.0          | 147.0 | 1200.0     |
| 15              | 2022-07-01 | 11:50:00  | 75          | Female | 42  | Electronics | 4        | 500.0          | 210.0 | 2000.0     |
| 743             | 2022-08-07 | 07:54:00  | 55          | Female | 34  | Beauty      | 4        | 500.0          | 260.0 | 2000.0     |
| 1015            | 2022-03-09 | 11:53:00  | 94          | Female | 42  | Electronics | 4        | 500.0          | 200.0 | 2000.0     |
| 1743            | 2022-10-26 | 09:37:00  | 47          | Female | 34  | Beauty      | 4        | 500.0          | 250.0 | 2000.0     |
| 742             | 2022-03-19 | 06:08:00  | 37          | Female | 38  | Electronics | 4        | 500.0          | 195.0 | 2000.0     |
| 1742            | 2022-11-22 | 08:25:00  | 18          | Female | 38  | Electronics | 4        | 500.0          | 220.0 | 2000.0     |
| 420             | 2022-01-02 | 10:53:00  | 28          | Female | 22  | Clothing    | 4        | 500.0          | 200.0 | 2000.0     |
| 1420            | 2022-04-15 | 07:01:00  | 138         | Female | 22  | Clothing    | 4        | 500.0          | 205.0 | 2000.0     |
| 592             | 2022-12-26 | 09:15:00  | 77          | Female | 46  | Beauty      | 4        | 500.0          | 275.0 | 2000.0     |
| 1592            | 2022-03-16 | 09:08:00  | 81          | Female | 46  | Beauty      | 4        | 500.0          | 155.0 | 2000.0     |
| 720             | 2022-04-08 | 08:50:00  | 116         | Female | 56  | Beauty      | 3        | 500.0          | 235.0 | 1500.0     |
| 1720            | 2022-10-10 | 08:51:00  | 28          | Female | 56  | Beauty      | 3        | 500.0          | 190.0 | 1500.0     |
| 269             | 2022-09-19 | 11:31:00  | 87          | Male   | 25  | Clothing    | 4        | 500.0          | 250.0 | 2000.0     |
| 320             | 2022-04-20 | 08:35:00  | 57          | Female | 28  | Electronics | 4        | 300.0          | 159.0 | 1200.0     |
| 673             | 2022-07-04 | 10:14:00  | 18          | Female | 43  | Clothing    | 3        | 500.0          | 270.0 | 1500.0     |
| 1269            | 2022-01-01 | 08:09:00  | 71          | Male   | 25  | Clothing    | 4        | 500.0          | 145.0 | 2000.0     |
| 1320            | 2022-11-02 | 11:55:00  | 102         | Female | 28  | Electronics | 4        | 300.0          | 84.0  | 1200.0     |
| 1673            | 2022-06-14 | 07:36:00  | 42          | Female | 43  | Clothing    | 3        | 500.0          | 185.0 | 1500.0     |
| 142             | 2022-04-08 | 10:05:00  | 61          | Male   | 35  | Electronics | 4        | 300.0          | 138.0 | 1200.0     |
| 1142            | 2022-11-09 | 09:49:00  | 2           | Male   | 35  | Electronics | 4        | 300.0          | 114.0 | 1200.0     |
| 107             | 2022-10-06 | 09:18:00  | 75          | Female | 21  | Clothing    | 4        | 300.0          | 78.0  | 1200.0     |
| 1107            | 2022-12-31 | 11:14:00  | 62          | Female | 21  | Clothing    | 4        | 300.0          | 102.0 | 1200.0     |
| 333             | 2022-10-06 | 08:15:00  | 21          | Female | 54  | Electronics | 4        | 300.0          | 99.0  | 1200.0     |
| 1333            | 2022-11-01 | 11:38:00  | 151         | Female | 54  | Electronics | 4        | 300.0          | 165.0 | 1200.0     |
| 372             | 2022-06-19 | 11:45:00  | 27          | Female | 24  | Beauty      | 3        | 500.0          | 140.0 | 1500.0     |
| 1372            | 2022-03-18 | 10:53:00  | 60          | Female | 24  | Beauty      | 3        | 500.0          | 145.0 | 1500.0     |
| 54              | 2022-10-20 | 10:17:00  | 142         | Female | 38  | Electronics | 3        | 500.0          | 200.0 | 1500.0     |
| 1054            | 2022-01-10 | 09:24:00  | 49          | Female | 38  | Electronics | 3        | 500.0          | 140.0 | 1500.0     |
| 193             | 2022-03-27 | 10:40:00  | 55          | Male   | 35  | Beauty      | 3        | 500.0          | 180.0 | 1500.0     |
| 577             | 2022-04-21 | 11:55:00  | 45          | Male   | 21  | Beauty      | 4        | 500.0          | 215.0 | 2000.0     |
| 1193            | 2022-05-11 | 11:31:00  | 50          | Male   | 35  | Beauty      | 3        | 500.0          | 145.0 | 1500.0     |
| 1577            | 2022-09-11 | 06:22:00  | 145         | Male   | 21  | Beauty      | 4        | 500.0          | 160.0 | 2000.0     |
| 16              | 2022-06-25 | 10:33:00  | 82          | Male   | 19  | Clothing    | 3        | 500.0          | 180.0 | 1500.0     |
| 292             | 2022-10-10 | 06:33:00  | 111         | Male   | 20  | Beauty      | 4        | 300.0          | 141.0 | 1200.0     |
| 416             | 2022-08-21 | 09:29:00  | 55          | Male   | 53  | Electronics | 4        | 500.0          | 245.0 | 2000.0     |
| 1016            | 2022-12-12 | 07:39:00  | 52          | Male   | 19  | Clothing    | 3        | 500.0          | 200.0 | 1500.0     |
| 1292            | 2022-05-15 | 08:20:00  | 88          | Male   | 20  | Beauty      | 4        | 300.0          | 90.0  | 1200.0     |
| 1416            | 2022-12-29 | 10:47:00  | 111         | Male   | 53  | Electronics | 4        | 500.0          | 125.0 | 2000.0     |
| 257             | 2022-12-10 | 08:49:00  | 130         | Male   | 19  | Beauty      | 4        | 500.0          | 165.0 | 2000.0     |
| 1257            | 2022-05-10 | 11:55:00  | 29          | Male   | 19  | Beauty      | 4        | 500.0          | 255.0 | 2000.0     |
| 611             | 2022-07-21 | 08:13:00  | 11          | Male   | 51  | Beauty      | 3        | 500.0          | 180.0 | 1500.0     |
| 800             | 2022-09-19 | 07:33:00  | 111         | Male   | 32  | Clothing    | 4        | 300.0          | 87.0  | 1200.0     |

---

### 6. Write a SQL query to find the total number of transactions (transaction_id) made by each gender in each category.

   
**SQL Query**

```sql
SELECT 
	category,gender,
	COUNT(*) AS total_transactions
FROM retail_sales
GROUP BY 1, 2
ORDER BY 1;

```

**Output**

| category    | gender | total_transactions |
|-------------|--------|--------------------|
| Beauty      | Female | 330                |
| Beauty      | Male   | 282                |
| Clothing    | Female | 347                |
| Clothing    | Male   | 354                |
| Electronics | Male   | 344                |
| Electronics | Female | 340                |

---

### 7. Write a SQL query to calculate the average sale for each month. Find out the best-selling month in each year.

   
**SQL Query**

```sql
SELECT 
	year,
	month,
	avg_total_sales
FROM 
(
	SELECT 	
		EXTRACT(YEAR FROM sale_date) AS year,
		EXTRACT(MONTH FROM sale_date) AS month,
		AVG(total_sale) AS avg_total_sales,
		RANK() OVER(PARTITION BY EXTRACT(YEAR FROM sale_date) ORDER BY AVG(total_sale) DESC) AS rank
	FROM retail_sales
	GROUP BY 1, 2
) as t1
WHERE rank = 1;
```

**Output**

| year | month | avg_total_sales   |
|------|-------|-------------------|
| 2022 | 7     | 541.3414634146342 |
| 2023 | 2     | 535.531914893617  |

---

### 8. Write a SQL query to find the top 5 customers based on the highest total sales.

   
**SQL Query**

```sql
SELECT 
	customer_id,
	SUM(total_sale) as total_sales
FROM retail_sales
GROUP BY 1
ORDER BY 2 DESC
LIMIT 5;
```

**Output**

| customer_id | total_sales |
|-------------|-------------|
| 3           | 38440.0     |
| 1           | 30750.0     |
| 5           | 30405.0     |
| 2           | 25295.0     |
| 4           | 23580.0     |

---

### 9. Write a SQL query to find the number of unique customers who purchased items from each category.

   
**SQL Query**

```sql
SELECT 
	category,
	COUNT(DISTINCT customer_id) as unique_customers
FROM retail_sales
GROUP BY category;
```

**Output**

| category    | unique_customers |
|-------------|------------------|
| Beauty      | 141              |
| Clothing    | 149              |
| Electronics | 144              |

---

### 10. Write a SQL query to create each shift and the number of orders (Example: Morning < 12, Afternoon Between 12 & 17, Evening > 17).

   
**SQL Query**

```sql
WITH hourly_sale 
AS
(
SELECT *,
CASE
	WHEN EXTRACT(HOUR FROM sale_time) < 12 THEN 'Morning'
	WHEN EXTRACT(HOUR FROM sale_time) BETWEEN 12 AND 17 THEN 'Afternoon'
	ELSE 'Evening'
END as shift
FROM retail_sales
)
SELECT 
	shift,
	COUNT(*) AS total_orders
FROM hourly_sale
GROUP BY shift
```

**Output**

| shift     | total_orders |
|-----------|--------------|
| Afternoon | 377          |
| Evening   | 1062         |
| Morning   | 558          |

---

## 💡 Key Insights

-   Electronics generated one of the highest revenues.
-   Clothing recorded the largest number of orders.
-   Beauty customers averaged approximately 40 years of age.
-   High-value transactions occurred across multiple categories.
-   Monthly and hourly trends can support demand forecasting.
  
---

# Findings

- **Customer Demographics**: The dataset includes customers from various age groups, with sales distributed across different categories such as Clothing and Beauty.
- **High-Value Transactions**: Several transactions had a total sale amount greater than 1000, indicating premium purchases.
- **Sales Trends**: Monthly analysis shows variations in sales, helping identify peak seasons.
- **Customer Insights**: The analysis identifies the top-spending customers and the most popular product categories.
  
---

# Reports

- **Sales Summary**: A detailed report summarizing total sales, customer demographics, and category performance.
- **Trend Analysis**: Insights into sales trends across different months and shifts.
- **Customer Insights**: Reports on top customers and unique customer counts per category.

---

# Conclusion

This project serves as a comprehensive introduction to SQL for data analysts, covering database setup, data cleaning, exploratory data analysis, and business-driven SQL queries. The findings from this project can help drive business decisions by providing insights into sales patterns, customer behaviour, and product performance.
