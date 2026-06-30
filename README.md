# Retail Sales Analysis SQL Project

## Project Overview

**Project Title**: Retail Sales Analysis  
**Database**: `retail_sales_SQL_project`

This project is designed to demonstrate SQL skills and techniques typically used by data analysts to explore, clean, and analyze retail sales data. The project involves setting up a retail sales database, performing exploratory data analysis (EDA), and answering specific business questions through SQL queries. This project is ideal for those who are starting their journey in data analysis and want to build a solid foundation in SQL.

## Objectives

1. **Set up a retail sales database**: Create and populate a retail sales database with the provided sales data.
2. **Data Cleaning**: Identify and remove any records with missing or null values.
3. **Exploratory Data Analysis (EDA)**: Perform basic exploratory data analysis to understand the dataset.
4. **Business Analysis**: Use SQL to answer specific business questions and derive insights from the sales data.

## Project Structure

### 1. Database Setup

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

### 2. Data Exploration & Cleaning

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

### 3.📈 Business Questions Solved


The following SQL queries were developed to answer specific business questions:

1. **Write a SQL query to retrieve all columns for sales made on '2022-11-05'. **

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


2. **Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 4 in the month of Nov-2022**.

   
**SQL Query**

```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Output**


3. **Write a SQL query to calculate the total sales (total_sale) for each category.**

 
**SQL Query**

```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Output**



4. **Write a SQL query to find the average age of customers who purchased items from the 'Beauty' category.**

   
**SQL Query**

```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Output**



5. **Write a SQL query to find all transactions where the total_sale is greater than 1000.**

   
**SQL Query**

```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Output**


6. **Write a SQL query to find the total number of transactions (transaction_id) made by each gender in each category.**

   
**SQL Query**

```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Output**


7. **Write a SQL query to calculate the average sale for each month. Find out the best-selling month in each year**

   
**SQL Query**

```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Output**



8. **Write a SQL query to find the top 5 customers based on the highest total sales **

   
**SQL Query**

```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Output**


9. **Write a SQL query to find the number of unique customers who purchased items from each category.**

   
**SQL Query**

```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Output**



10. **Write a SQL query to create each shift and number of orders (Example: Morning <12, Afternoon Between 12 & 17, Evening >17)**

   
**SQL Query**

```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';
```

**Output**



## Findings

- **Customer Demographics**: The dataset includes customers from various age groups, with sales distributed across different categories such as Clothing and Beauty.
- **High-Value Transactions**: Several transactions had a total sale amount greater than 1000, indicating premium purchases.
- **Sales Trends**: Monthly analysis shows variations in sales, helping identify peak seasons.
- **Customer Insights**: The analysis identifies the top-spending customers and the most popular product categories.

## Reports

- **Sales Summary**: A detailed report summarizing total sales, customer demographics, and category performance.
- **Trend Analysis**: Insights into sales trends across different months and shifts.
- **Customer Insights**: Reports on top customers and unique customer counts per category.

## Conclusion

This project serves as a comprehensive introduction to SQL for data analysts, covering database setup, data cleaning, exploratory data analysis, and business-driven SQL queries. The findings from this project can help drive business decisions by providing insights into sales patterns, customer behaviour, and product performance.
