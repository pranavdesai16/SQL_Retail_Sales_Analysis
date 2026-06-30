# Retail Sales Analysis SQL Project

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
| 1611            | 2022-11-17 | 07:30:00  | 125         | Male   | 51  | Beauty      | 3        | 500.0          | 180.0 | 1500.0     |
| 1800            | 2022-08-21 | 10:53:00  | 1           | Male   | 32  | Clothing    | 4        | 300.0          | 111.0 | 1200.0     |
| 506             | 2022-04-29 | 07:13:00  | 9           | Male   | 34  | Beauty      | 3        | 500.0          | 200.0 | 1500.0     |
| 1506            | 2022-01-09 | 07:31:00  | 52          | Male   | 34  | Beauty      | 3        | 500.0          | 245.0 | 1500.0     |
| 152             | 2022-06-16 | 11:58:00  | 120         | Male   | 43  | Electronics | 4        | 500.0          | 210.0 | 2000.0     |
| 1152            | 2022-12-26 | 07:48:00  | 87          | Male   | 43  | Electronics | 4        | 500.0          | 170.0 | 2000.0     |
| 547             | 2022-11-14 | 07:36:00  | 3           | Male   | 63  | Clothing    | 4        | 500.0          | 250.0 | 2000.0     |
| 1547            | 2022-08-11 | 06:39:00  | 142         | Male   | 63  | Clothing    | 4        | 500.0          | 235.0 | 2000.0     |
| 942             | 2023-12-01 | 09:22:00  | 35          | Male   | 51  | Clothing    | 3        | 500.0          | 160.0 | 1500.0     |
| 1942            | 2023-09-16 | 11:53:00  | 112         | Male   | 51  | Clothing    | 3        | 500.0          | 265.0 | 1500.0     |
| 663             | 2023-08-16 | 06:32:00  | 133         | Male   | 23  | Clothing    | 4        | 300.0          | 87.0  | 1200.0     |
| 1663            | 2023-12-07 | 07:04:00  | 33          | Male   | 23  | Clothing    | 4        | 300.0          | 81.0  | 1200.0     |
| 313             | 2023-12-16 | 10:03:00  | 11          | Female | 55  | Beauty      | 3        | 500.0          | 140.0 | 1500.0     |
| 459             | 2023-05-23 | 07:12:00  | 122         | Male   | 28  | Clothing    | 4        | 300.0          | 75.0  | 1200.0     |
| 1313            | 2023-06-04 | 09:22:00  | 10          | Female | 55  | Beauty      | 3        | 500.0          | 170.0 | 1500.0     |
| 1459            | 2023-11-10 | 06:46:00  | 13          | Male   | 28  | Clothing    | 4        | 300.0          | 144.0 | 1200.0     |
| 636             | 2023-05-09 | 06:15:00  | 60          | Female | 21  | Beauty      | 3        | 500.0          | 230.0 | 1500.0     |
| 1636            | 2023-07-22 | 11:26:00  | 50          | Female | 21  | Beauty      | 3        | 500.0          | 150.0 | 1500.0     |
| 202             | 2023-01-25 | 06:24:00  | 61          | Female | 34  | Clothing    | 4        | 300.0          | 120.0 | 1200.0     |
| 1202            | 2023-11-13 | 06:56:00  | 89          | Female | 34  | Clothing    | 4        | 300.0          | 144.0 | 1200.0     |
| 553             | 2023-03-20 | 06:17:00  | 106         | Male   | 24  | Clothing    | 4        | 300.0          | 81.0  | 1200.0     |
| 1553            | 2023-01-29 | 08:46:00  | 42          | Male   | 24  | Clothing    | 4        | 300.0          | 99.0  | 1200.0     |
| 462             | 2023-08-26 | 10:04:00  | 71          | Male   | 63  | Electronics | 4        | 300.0          | 132.0 | 1200.0     |
| 614             | 2023-02-13 | 06:28:00  | 61          | Female | 39  | Beauty      | 4        | 300.0          | 120.0 | 1200.0     |
| 808             | 2023-11-22 | 07:18:00  | 30          | Male   | 33  | Beauty      | 4        | 500.0          | 195.0 | 2000.0     |
| 1462            | 2023-11-13 | 10:42:00  | 124         | Male   | 63  | Electronics | 4        | 300.0          | 114.0 | 1200.0     |
| 1614            | 2023-08-23 | 11:37:00  | 135         | Female | 39  | Beauty      | 4        | 300.0          | 105.0 | 1200.0     |
| 1808            | 2023-02-12 | 10:48:00  | 109         | Male   | 33  | Beauty      | 4        | 500.0          | 210.0 | 2000.0     |
| 166             | 2023-01-28 | 11:42:00  | 32          | Male   | 34  | Clothing    | 4        | 500.0          | 225.0 | 2000.0     |
| 1166            | 2023-07-19 | 07:45:00  | 65          | Male   | 34  | Clothing    | 4        | 500.0          | 245.0 | 2000.0     |
| 280             | 2023-11-17 | 09:35:00  | 76          | Female | 37  | Clothing    | 3        | 500.0          | 240.0 | 1500.0     |
| 1280            | 2023-08-24 | 09:15:00  | 116         | Female | 37  | Clothing    | 3        | 500.0          | 255.0 | 1500.0     |
| 928             | 2023-11-05 | 10:20:00  | 54          | Female | 35  | Clothing    | 4        | 300.0          | 90.0  | 1200.0     |
| 1928            | 2023-07-29 | 06:39:00  | 93          | Female | 35  | Clothing    | 4        | 300.0          | 75.0  | 1200.0     |
| 332             | 2023-04-24 | 11:28:00  | 138         | Male   | 58  | Electronics | 4        | 300.0          | 105.0 | 1200.0     |
| 1332            | 2023-12-04 | 10:02:00  | 146         | Male   | 58  | Electronics | 4        | 300.0          | 123.0 | 1200.0     |
| 847             | 2023-01-10 | 08:42:00  | 2           | Female | 18  | Electronics | 4        | 300.0          | 162.0 | 1200.0     |
| 1847            | 2023-07-28 | 07:14:00  | 5           | Female | 18  | Electronics | 4        | 300.0          | 123.0 | 1200.0     |
| 111             | 2023-04-15 | 09:45:00  | 5           | Female | 34  | Electronics | 3        | 500.0          | 130.0 | 1500.0     |
| 1111            | 2023-04-30 | 21:34:00  | 2           | Female | 34  | Electronics | 3        | 500.0          | 185.0 | 1500.0     |
| 298             | 2023-10-05 | 19:05:00  | 3           | Male   | 27  | Beauty      | 4        | 300.0          | 84.0  | 1200.0     |
| 572             | 2023-12-13 | 18:33:00  | 5           | Male   | 31  | Clothing    | 4        | 500.0          | 185.0 | 2000.0     |
| 1298            | 2023-05-02 | 19:51:00  | 1           | Male   | 27  | Beauty      | 4        | 300.0          | 120.0 | 1200.0     |
| 1572            | 2023-06-18 | 22:20:00  | 1           | Male   | 31  | Clothing    | 4        | 500.0          | 175.0 | 2000.0     |
| 693             | 2023-06-08 | 17:12:00  | 1           | Male   | 41  | Beauty      | 3        | 500.0          | 270.0 | 1500.0     |
| 1693            | 2023-02-20 | 18:21:00  | 1           | Male   | 41  | Beauty      | 3        | 500.0          | 130.0 | 1500.0     |
| 482             | 2023-08-12 | 18:57:00  | 3           | Female | 28  | Clothing    | 4        | 300.0          | 141.0 | 1200.0     |
| 1482            | 2023-02-10 | 22:22:00  | 1           | Female | 28  | Clothing    | 4        | 300.0          | 114.0 | 1200.0     |
| 452             | 2023-01-30 | 22:41:00  | 4           | Female | 48  | Clothing    | 3        | 500.0          | 240.0 | 1500.0     |
| 946             | 2023-08-08 | 20:15:00  | 2           | Male   | 62  | Electronics | 4        | 500.0          | 235.0 | 2000.0     |
| 1452            | 2023-08-06 | 17:41:00  | 3           | Female | 48  | Clothing    | 3        | 500.0          | 185.0 | 1500.0     |
| 1946            | 2023-07-27 | 20:48:00  | 5           | Male   | 62  | Electronics | 4        | 500.0          | 165.0 | 2000.0     |
| 731             | 2023-09-30 | 18:49:00  | 1           | Male   | 54  | Clothing    | 4        | 500.0          | 165.0 | 2000.0     |
| 1731            | 2023-12-19 | 17:41:00  | 3           | Male   | 54  | Clothing    | 4        | 500.0          | 195.0 | 2000.0     |
| 164             | 2023-02-28 | 18:26:00  | 3           | Female | 47  | Beauty      | 3        | 500.0          | 185.0 | 1500.0     |
| 1164            | 2023-04-07 | 20:53:00  | 1           | Female | 47  | Beauty      | 3        | 500.0          | 245.0 | 1500.0     |
| 118             | 2023-03-13 | 20:07:00  | 3           | Female | 30  | Electronics | 4        | 500.0          | 270.0 | 2000.0     |
| 970             | 2023-05-25 | 18:13:00  | 2           | Male   | 59  | Electronics | 4        | 500.0          | 220.0 | 2000.0     |
| 1118            | 2023-10-13 | 17:24:00  | 1           | Female | 30  | Electronics | 4        | 500.0          | 170.0 | 2000.0     |
| 1970            | 2023-05-22 | 17:44:00  | 5           | Male   | 59  | Electronics | 4        | 500.0          | 230.0 | 2000.0     |
| 155             | 2023-07-18 | 18:05:00  | 3           | Male   | 31  | Electronics | 4        | 500.0          | 150.0 | 2000.0     |
| 1155            | 2023-12-03 | 18:22:00  | 3           | Male   | 31  | Electronics | 4        | 500.0          | 255.0 | 2000.0     |
| 647             | 2023-03-01 | 19:53:00  | 5           | Male   | 59  | Clothing    | 3        | 500.0          | 190.0 | 1500.0     |
| 1647            | 2023-05-01 | 20:26:00  | 5           | Male   | 59  | Clothing    | 3        | 500.0          | 240.0 | 1500.0     |
| 843             | 2023-01-25 | 22:46:00  | 3           | Male   | 21  | Beauty      | 3        | 500.0          | 180.0 | 1500.0     |
| 1843            | 2023-09-21 | 18:58:00  | 1           | Male   | 21  | Beauty      | 3        | 500.0          | 240.0 | 1500.0     |
| 31              | 2023-12-31 | 17:47:00  | 3           | Male   | 44  | Electronics | 4        | 300.0          | 129.0 | 1200.0     |
| 72              | 2023-12-06 | 19:19:00  | 5           | Female | 20  | Electronics | 4        | 500.0          | 195.0 | 2000.0     |
| 281             | 2023-09-18 | 20:09:00  | 4           | Female | 29  | Beauty      | 4        | 500.0          | 275.0 | 2000.0     |
| 729             | 2023-08-26 | 22:29:00  | 3           | Male   | 29  | Clothing    | 4        | 300.0          | 84.0  | 1200.0     |
| 1031            | 2023-11-12 | 21:15:00  | 3           | Male   | 44  | Electronics | 4        | 300.0          | 126.0 | 1200.0     |
| 1072            | 2023-02-24 | 18:10:00  | 4           | Female | 20  | Electronics | 4        | 500.0          | 180.0 | 2000.0     |
| 1281            | 2023-03-14 | 19:34:00  | 4           | Female | 29  | Beauty      | 4        | 500.0          | 165.0 | 2000.0     |
| 1729            | 2023-11-22 | 18:55:00  | 82          | Male   | 29  | Clothing    | 4        | 300.0          | 81.0  | 1200.0     |
| 561             | 2022-07-29 | 17:04:00  | 34          | Female | 64  | Clothing    | 4        | 500.0          | 250.0 | 2000.0     |
| 1561            | 2023-09-17 | 19:38:00  | 16          | Female | 64  | Clothing    | 4        | 500.0          | 170.0 | 2000.0     |
| 67              | 2023-08-19 | 20:19:00  | 119         | Female | 48  | Beauty      | 4        | 300.0          | 129.0 | 1200.0     |
| 1067            | 2023-10-03 | 17:01:00  | 105         | Female | 48  | Beauty      | 4        | 300.0          | 129.0 | 1200.0     |
| 862             | 2022-12-11 | 21:37:00  | 29          | Male   | 28  | Electronics | 4        | 300.0          | 78.0  | 1200.0     |
| 1862            | 2022-02-06 | 22:50:00  | 64          | Male   | 28  | Electronics | 4        | 300.0          | 165.0 | 1200.0     |
| 481             | 2023-07-13 | 17:12:00  | 48          | Female | 43  | Electronics | 4        | 300.0          | 114.0 | 1200.0     |
| 1481            | 2023-11-09 | 17:22:00  | 20          | Female | 43  | Electronics | 4        | 300.0          | 114.0 | 1200.0     |
| 587             | 2023-09-04 | 19:00:00  | 91          | Female | 40  | Beauty      | 4        | 300.0          | 99.0  | 1200.0     |
| 1587            | 2022-11-05 | 20:06:00  | 140         | Female | 40  | Beauty      | 4        | 300.0          | 105.0 | 1200.0     |
| 212             | 2023-10-12 | 18:13:00  | 105         | Male   | 21  | Clothing    | 3        | 500.0          | 215.0 | 1500.0     |
| 1212            | 2022-03-16 | 18:05:00  | 142         | Male   | 21  | Clothing    | 3        | 500.0          | 265.0 | 1500.0     |
| 356             | 2023-08-27 | 18:35:00  | 71          | Male   | 50  | Electronics | 3        | 500.0          | 255.0 | 1500.0     |
| 1356            | 2023-12-18 | 21:31:00  | 11          | Male   | 50  | Electronics | 3        | 500.0          | 245.0 | 1500.0     |
| 726             | 2022-06-05 | 19:37:00  | 72          | Male   | 47  | Clothing    | 4        | 300.0          | 126.0 | 1200.0     |
| 1726            | 2023-06-26 | 18:12:00  | 13          | Male   | 47  | Clothing    | 4        | 300.0          | 93.0  | 1200.0     |
| 239             | 2022-09-19 | 19:34:00  | 1           | Male   | 38  | Electronics | 3        | 500.0          | 165.0 | 1500.0     |
| 669             | 2022-01-23 | 20:24:00  | 110         | Male   | 24  | Beauty      | 4        | 300.0          | 87.0  | 1200.0     |
| 1239            | 2022-07-08 | 20:42:00  | 134         | Male   | 38  | Electronics | 3        | 500.0          | 255.0 | 1500.0     |
| 1669            | 2022-08-04 | 22:28:00  | 83          | Male   | 24  | Beauty      | 4        | 300.0          | 123.0 | 1200.0     |
| 157             | 2022-05-15 | 21:59:00  | 98          | Male   | 62  | Electronics | 4        | 500.0          | 170.0 | 2000.0     |
| 839             | 2023-11-11 | 21:02:00  | 130         | Female | 20  | Electronics | 4        | 300.0          | 96.0  | 1200.0     |
| 927             | 2022-02-21 | 17:13:00  | 83          | Male   | 43  | Electronics | 4        | 500.0          | 250.0 | 2000.0     |
| 1157            | 2022-12-23 | 21:24:00  | 81          | Male   | 62  | Electronics | 4        | 500.0          | 270.0 | 2000.0     |
| 1839            | 2022-08-28 | 21:57:00  | 92          | Female | 20  | Electronics | 4        | 300.0          | 156.0 | 1200.0     |
| 1927            | 2023-09-06 | 19:44:00  | 46          | Male   | 43  | Electronics | 4        | 500.0          | 180.0 | 2000.0     |
| 46              | 2022-11-08 | 17:50:00  | 54          | Female | 20  | Electronics | 4        | 300.0          | 84.0  | 1200.0     |
| 1046            | 2023-07-21 | 21:47:00  | 5           | Female | 20  | Electronics | 4        | 300.0          | 156.0 | 1200.0     |
| 480             | 2022-12-22 | 22:12:00  | 126         | Female | 42  | Beauty      | 4        | 500.0          | 225.0 | 2000.0     |
| 1480            | 2023-11-26 | 18:05:00  | 3           | Female | 42  | Beauty      | 4        | 500.0          | 165.0 | 2000.0     |
| 78              | 2023-02-17 | 21:08:00  | 68          | Female | 47  | Clothing    | 3        | 500.0          | 265.0 | 1500.0     |
| 1078            | 2023-05-04 | 22:20:00  | 16          | Female | 47  | Clothing    | 3        | 500.0          | 125.0 | 1500.0     |
| 447             | 2023-04-18 | 17:57:00  | 37          | Male   | 22  | Beauty      | 4        | 500.0          | 245.0 | 2000.0     |
| 1447            | 2022-05-30 | 22:21:00  | 137         | Male   | 22  | Beauty      | 4        | 500.0          | 155.0 | 2000.0     |
| 93              | 2022-01-25 | 20:52:00  | 148         | Female | 35  | Beauty      | 4        | 500.0          | 140.0 | 2000.0     |
| 1093            | 2023-11-06 | 17:26:00  | 87          | Female | 35  | Beauty      | 4        | 500.0          | 270.0 | 2000.0     |
| 144             | 2022-03-26 | 22:18:00  | 119         | Female | 59  | Beauty      | 3        | 500.0          | 255.0 | 1500.0     |
| 474             | 2022-05-08 | 17:57:00  | 145         | Female | 26  | Clothing    | 3        | 500.0          | 210.0 | 1500.0     |
| 1144            | 2022-12-30 | 21:27:00  | 148         | Female | 59  | Beauty      | 3        | 500.0          | 125.0 | 1500.0     |
| 1474            | 2022-05-15 | 20:49:00  | 84          | Female | 26  | Clothing    | 3        | 500.0          | 255.0 | 1500.0     |
| 676             | 2023-07-10 | 22:13:00  | 80          | Male   | 63  | Electronics | 3        | 500.0          | 205.0 | 1500.0     |
| 1676            | 2023-09-21 | 20:22:00  | 91          | Male   | 63  | Electronics | 3        | 500.0          | 210.0 | 1500.0     |
| 773             | 2023-01-14 | 19:10:00  | 3           | Male   | 25  | Electronics | 4        | 500.0          | 175.0 | 2000.0     |
| 1773            | 2023-12-12 | 18:50:00  | 80          | Male   | 25  | Electronics | 4        | 500.0          | 165.0 | 2000.0     |
| 213             | 2023-08-13 | 20:48:00  | 113         | Male   | 27  | Beauty      | 3        | 500.0          | 275.0 | 1500.0     |
| 487             | 2023-04-09 | 21:03:00  | 36          | Male   | 44  | Clothing    | 4        | 500.0          | 235.0 | 2000.0     |
| 1213            | 2023-06-21 | 17:23:00  | 41          | Male   | 27  | Beauty      | 3        | 500.0          | 185.0 | 1500.0     |
| 1487            | 2023-02-01 | 19:01:00  | 131         | Male   | 44  | Clothing    | 4        | 500.0          | 140.0 | 2000.0     |
| 463             | 2023-01-29 | 20:22:00  | 55          | Female | 54  | Beauty      | 3        | 500.0          | 175.0 | 1500.0     |
| 1463            | 2022-07-29 | 19:45:00  | 98          | Female | 54  | Beauty      | 3        | 500.0          | 170.0 | 1500.0     |
| 13              | 2023-02-08 | 17:43:00  | 106         | Male   | 22  | Electronics | 3        | 500.0          | 245.0 | 1500.0     |
| 308             | 2022-03-31 | 19:12:00  | 130         | Female | 34  | Beauty      | 4        | 300.0          | 126.0 | 1200.0     |
| 1013            | 2022-07-16 | 19:38:00  | 111         | Male   | 22  | Electronics | 3        | 500.0          | 200.0 | 1500.0     |
| 1308            | 2023-06-19 | 22:39:00  | 91          | Female | 34  | Beauty      | 4        | 300.0          | 150.0 | 1200.0     |
| 875             | 2023-11-30 | 21:47:00  | 134         | Female | 51  | Electronics | 4        | 500.0          | 135.0 | 2000.0     |
| 1875            | 2022-06-03 | 22:42:00  | 141         | Female | 51  | Electronics | 4        | 500.0          | 165.0 | 2000.0     |
| 716             | 2023-08-13 | 19:51:00  | 137         | Female | 60  | Clothing    | 4        | 300.0          | 108.0 | 1200.0     |
| 1716            | 2022-02-12 | 19:16:00  | 39          | Female | 60  | Clothing    | 4        | 300.0          | 87.0  | 1200.0     |
| 648             | 2023-02-23 | 18:13:00  | 41          | Male   | 53  | Beauty      | 4        | 300.0          | 138.0 | 1200.0     |
| 1648            | 2023-07-10 | 17:18:00  | 16          | Male   | 53  | Beauty      | 4        | 300.0          | 87.0  | 1200.0     |
| 859             | 2022-09-20 | 21:52:00  | 46          | Female | 56  | Electronics | 3        | 500.0          | 190.0 | 1500.0     |
| 1859            | 2022-09-14 | 20:58:00  | 32          | Female | 56  | Electronics | 3        | 500.0          | 205.0 | 1500.0     |
| 956             | 2023-04-24 | 21:50:00  | 140         | Male   | 30  | Clothing    | 3        | 500.0          | 135.0 | 1500.0     |
| 1956            | 2023-06-01 | 20:40:00  | 62          | Male   | 30  | Clothing    | 3        | 500.0          | 170.0 | 1500.0     |
| 597             | 2022-11-01 | 19:29:00  | 84          | Male   | 22  | Beauty      | 4        | 300.0          | 111.0 | 1200.0     |
| 1597            | 2023-08-28 | 18:21:00  | 32          | Male   | 22  | Beauty      | 4        | 300.0          | 78.0  | 1200.0     |
| 368             | 2023-01-31 | 21:11:00  | 90          | Female | 56  | Clothing    | 4        | 300.0          | 132.0 | 1200.0     |
| 1368            | 2022-03-08 | 21:29:00  | 145         | Female | 56  | Clothing    | 4        | 300.0          | 132.0 | 1200.0     |
| 479             | 2022-11-03 | 21:35:00  | 90          | Male   | 52  | Electronics | 4        | 300.0          | 105.0 | 1200.0     |
| 1479            | 2022-05-31 | 22:24:00  | 108         | Male   | 52  | Electronics | 4        | 300.0          | 162.0 | 1200.0     |
| 756             | 2023-07-17 | 20:33:00  | 4           | Female | 62  | Electronics | 4        | 300.0          | 333.0 | 1200.0     |
| 1756            | 2022-05-12 | 22:16:00  | 119         | Female | 62  | Electronics | 4        | 300.0          | 297.0 | 1200.0     |
| 476             | 2023-12-12 | 18:31:00  | 131         | Female | 27  | Clothing    | 4        | 500.0          | 570.0 | 2000.0     |
| 1476            | 2022-11-11 | 22:27:00  | 130         | Female | 27  | Clothing    | 4        | 500.0          | 555.0 | 2000.0     |
| 253             | 2022-09-30 | 21:26:00  | 66          | Female | 53  | Clothing    | 4        | 500.0          | 525.0 | 2000.0     |
| 1253            | 2023-12-03 | 19:58:00  | 108         | Female | 53  | Clothing    | 4        | 500.0          | 605.0 | 2000.0     |
| 682             | 2023-10-23 | 20:51:00  | 60          | Male   | 46  | Beauty      | 4        | 300.0          | 354.0 | 1200.0     |
| 1682            | 2022-12-30 | 19:30:00  | 71          | Male   | 46  | Beauty      | 4        | 300.0          | 315.0 | 1200.0     |
| 296             | 2022-12-31 | 22:44:00  | 73          | Female | 22  | Clothing    | 4        | 300.0          | 369.0 | 1200.0     |
| 1296            | 2022-11-26 | 20:42:00  | 45          | Female | 22  | Clothing    | 4        | 300.0          | 342.0 | 1200.0     |
| 832             | 2022-11-13 | 17:25:00  | 106         | Male   | 47  | Beauty      | 4        | 500.0          | 600.0 | 2000.0     |
| 1832            | 2023-11-10 | 21:17:00  | 57          | Male   | 47  | Beauty      | 4        | 500.0          | 480.0 | 2000.0     |
| 165             | 2022-09-24 | 19:01:00  | 75          | Female | 60  | Clothing    | 4        | 300.0          | 318.0 | 1200.0     |
| 1165            | 2023-12-01 | 17:04:00  | 29          | Female | 60  | Clothing    | 4        | 300.0          | 291.0 | 1200.0     |
| 412             | 2022-09-04 | 19:36:00  | 30          | Female | 19  | Electronics | 4        | 500.0          | 570.0 | 2000.0     |
| 1412            | 2022-10-13 | 19:59:00  | 75          | Female | 19  | Electronics | 4        | 500.0          | 615.0 | 2000.0     |
| 626             | 2022-10-30 | 21:01:00  | 65          | Female | 26  | Clothing    | 4        | 500.0          | 555.0 | 2000.0     |
| 1626            | 2022-10-10 | 19:13:00  | 19          | Female | 26  | Clothing    | 4        | 500.0          | 495.0 | 2000.0     |
| 789             | 2023-12-06 | 22:13:00  | 34          | Female | 61  | Clothing    | 4        | 500.0          | 510.0 | 2000.0     |
| 1789            | 2023-11-10 | 17:02:00  | 144         | Female | 61  | Clothing    | 4        | 500.0          | 615.0 | 2000.0     |
| 89              | 2023-12-30 | 21:15:00  | 117         | Female | 55  | Electronics | 4        | 500.0          | 590.0 | 2000.0     |
| 1089            | 2023-10-21 | 18:44:00  | 108         | Female | 55  | Electronics | 4        | 500.0          | 555.0 | 2000.0     |
| 524             | 2023-09-17 | 19:52:00  | 12          | Male   | 46  | Beauty      | 4        | 300.0          | 297.0 | 1200.0     |
| 1524            | 2022-10-26 | 22:10:00  | 115         | Male   | 46  | Beauty      | 4        | 300.0          | 321.0 | 1200.0     |
| 735             | 2022-11-26 | 21:38:00  | 153         | Female | 64  | Clothing    | 4        | 500.0          | 515.0 | 2000.0     |
| 1735            | 2023-09-05 | 17:26:00  | 86          | Female | 64  | Clothing    | 4        | 500.0          | 505.0 | 2000.0     |
| 385             | 2022-11-20 | 19:06:00  | 127         | Male   | 50  | Electronics | 3        | 500.0          | 525.0 | 1500.0     |
| 1385            | 2023-11-07 | 19:22:00  | 55          | Male   | 50  | Electronics | 3        | 500.0          | 505.0 | 1500.0     |
| 437             | 2023-11-26 | 18:53:00  | 56          | Female | 35  | Electronics | 4        | 300.0          | 345.0 | 1200.0     |
| 1437            | 2023-09-04 | 19:19:00  | 76          | Female | 35  | Electronics | 4        | 300.0          | 372.0 | 1200.0     |
| 634             | 2022-10-10 | 19:25:00  | 68          | Male   | 60  | Electronics | 4        | 500.0          | 535.0 | 2000.0     |
| 1634            | 2023-11-03 | 17:18:00  | 90          | Male   | 60  | Electronics | 4        | 500.0          | 520.0 | 2000.0     |
| 441             | 2023-11-06 | 22:00:00  | 85          | Male   | 57  | Beauty      | 4        | 300.0          | 351.0 | 1200.0     |
| 1441            | 2023-10-04 | 21:38:00  | 63          | Male   | 57  | Beauty      | 4        | 300.0          | 354.0 | 1200.0     |
| 431             | 2022-10-29 | 22:02:00  | 99          | Male   | 63  | Electronics | 4        | 300.0          | 345.0 | 1200.0     |
| 1431            | 2023-09-28 | 21:28:00  | 114         | Male   | 63  | Electronics | 4        | 300.0          | 312.0 | 1200.0     |
| 711             | 2023-09-23 | 22:26:00  | 103         | Male   | 26  | Electronics | 3        | 500.0          | 575.0 | 1500.0     |
| 943             | 2022-11-05 | 19:29:00  | 90          | Female | 57  | Clothing    | 4        | 300.0          | 318.0 | 1200.0     |
| 1711            | 2023-09-22 | 20:33:00  | 113         | Male   | 26  | Electronics | 3        | 500.0          | 570.0 | 1500.0     |
| 1943            | 2023-11-17 | 21:00:00  | 108         | Female | 57  | Clothing    | 4        | 300.0          | 321.0 | 1200.0     |
| 109             | 2023-09-06 | 19:57:00  | 94          | Female | 34  | Electronics | 4        | 500.0          | 560.0 | 2000.0     |
| 1109            | 2023-12-13 | 22:13:00  | 114         | Female | 34  | Electronics | 4        | 500.0          | 590.0 | 2000.0     |
| 340             | 2023-09-19 | 22:59:00  | 54          | Female | 36  | Clothing    | 4        | 300.0          | 294.0 | 1200.0     |
| 1340            | 2023-10-30 | 20:55:00  | 92          | Female | 36  | Clothing    | 4        | 300.0          | 348.0 | 1200.0     |
| 342             | 2023-11-05 | 17:24:00  | 85          | Female | 43  | Clothing    | 4        | 500.0          | 500.0 | 2000.0     |
| 1342            | 2022-09-18 | 23:00:00  | 114         | Female | 43  | Clothing    | 4        | 500.0          | 485.0 | 2000.0     |
| 503             | 2023-10-08 | 20:06:00  | 63          | Male   | 45  | Beauty      | 4        | 500.0          | 570.0 | 2000.0     |
| 869             | 2022-09-08 | 22:16:00  | 51          | Male   | 37  | Beauty      | 3        | 500.0          | 485.0 | 1500.0     |
| 1503            | 2022-10-17 | 18:28:00  | 67          | Male   | 45  | Beauty      | 4        | 500.0          | 605.0 | 2000.0     |
| 1869            | 2022-10-23 | 19:51:00  | 113         | Male   | 37  | Beauty      | 3        | 500.0          | 605.0 | 1500.0     |
| 124             | 2022-12-24 | 21:17:00  | 83          | Male   | 33  | Clothing    | 4        | 500.0          | 515.0 | 2000.0     |
| 677             | 2022-12-17 | 21:13:00  | 65          | Female | 19  | Beauty      | 3        | 500.0          | 555.0 | 1500.0     |
| 1124            | 2023-10-06 | 20:04:00  | 83          | Male   | 33  | Clothing    | 4        | 500.0          | 515.0 | 2000.0     |
| 1677            | 2022-10-02 | 20:51:00  | 84          | Female | 19  | Beauty      | 3        | 500.0          | 490.0 | 1500.0     |
| 710             | 2022-09-03 | 21:11:00  | 71          | Female | 26  | Electronics | 3        | 500.0          | 495.0 | 1500.0     |
| 1710            | 2022-10-23 | 20:14:00  | 104         | Female | 26  | Electronics | 3        | 500.0          | 610.0 | 1500.0     |
| 507             | 2022-12-11 | 21:40:00  | 52          | Female | 37  | Electronics | 3        | 500.0          | 485.0 | 1500.0     |
| 1507            | 2022-12-27 | 22:14:00  | 95          | Female | 37  | Electronics | 3        | 500.0          | 520.0 | 1500.0     |
| 181             | 2023-11-06 | 19:59:00  | 79          | Male   | 19  | Electronics | 4        | 300.0          | 327.0 | 1200.0     |
| 1181            | 2022-11-06 | 18:28:00  | 84          | Male   | 19  | Electronics | 4        | 300.0          | 354.0 | 1200.0     |
| 47              | 2022-10-22 | 17:22:00  | 96          | Female | 40  | Beauty      | 3        | 500.0          | 600.0 | 1500.0     |
| 405             | 2022-10-17 | 17:55:00  | 79          | Female | 25  | Clothing    | 4        | 300.0          | 324.0 | 1200.0     |
| 1047            | 2022-12-04 | 21:53:00  | 84          | Female | 40  | Beauty      | 3        | 500.0          | 490.0 | 1500.0     |
| 1405            | 2023-10-28 | 20:08:00  | 91          | Female | 25  | Clothing    | 4        | 300.0          | 342.0 | 1200.0     |
| 595             | 2022-10-15 | 21:35:00  | 65          | Female | 18  | Clothing    | 4        | 500.0          | 210.0 | 2000.0     |
| 1595            | 2023-10-04 | 17:44:00  | 115         | Female | 18  | Clothing    | 4        | 500.0          | 255.0 | 2000.0     |
| 58              | 2023-09-16 | 19:18:00  | 53          | Male   | 18  | Clothing    | 4        | 300.0          | 75.0  | 1200.0     |
| 1058            | 2022-10-30 | 18:31:00  | 100         | Male   | 18  | Clothing    | 4        | 300.0          | 153.0 | 1200.0     |
| 369             | 2023-12-13 | 19:42:00  | 111         | Male   | 23  | Electronics | 3        | 500.0          | 215.0 | 1500.0     |
| 1369            | 2022-10-10 | 21:14:00  | 64          | Male   | 23  | Electronics | 3        | 500.0          | 180.0 | 1500.0     |
| 533             | 2022-11-13 | 17:19:00  | 92          | Male   | 19  | Electronics | 3        | 500.0          | 155.0 | 1500.0     |
| 1533            | 2022-10-29 | 19:35:00  | 67          | Male   | 19  | Electronics | 3        | 500.0          | 255.0 | 1500.0     |
| 169             | 2022-11-28 | 18:47:00  | 73          | Male   | 18  | Beauty      | 3        | 500.0          | 145.0 | 1500.0     |
| 1169            | 2022-09-25 | 17:12:00  | 101         | Male   | 18  | Beauty      | 3        | 500.0          | 255.0 | 1500.0     |
| 74              | 2023-10-05 | 19:50:00  | 56          | Female | 18  | Beauty      | 4        | 500.0          | 205.0 | 2000.0     |
| 1074            | 2022-10-04 | 20:18:00  | 67          | Female | 18  | Beauty      | 4        | 500.0          | 230.0 | 2000.0     |
| 424             | 2023-12-20 | 19:21:00  | 101         | Male   | 57  | Beauty      | 4        | 300.0          | 147.0 | 1200.0     |
| 1424            | 2023-09-05 | 21:32:00  | 54          | Male   | 57  | Beauty      | 4        | 300.0          | 111.0 | 1200.0     |
| 115             | 2022-09-02 | 19:21:00  | 67          | Male   | 51  | Clothing    | 3        | 500.0          | 255.0 | 1500.0     |
| 1115            | 2023-09-21 | 17:41:00  | 99          | Male   | 51  | Clothing    | 3        | 500.0          | 180.0 | 1500.0     |
| 215             | 2022-10-03 | 21:20:00  | 101         | Male   | 58  | Clothing    | 3        | 500.0          | 145.0 | 1500.0     |
| 1215            | 2022-11-19 | 20:44:00  | 107         | Male   | 58  | Clothing    | 3        | 500.0          | 130.0 | 1500.0     |
| 112             | 2023-12-25 | 18:44:00  | 57          | Male   | 37  | Clothing    | 3        | 500.0          | 165.0 | 1500.0     |
| 608             | 2022-12-07 | 22:19:00  | 112         | Female | 55  | Electronics | 3        | 500.0          | 200.0 | 1500.0     |
| 1112            | 2022-12-22 | 17:11:00  | 94          | Male   | 37  | Clothing    | 3        | 500.0          | 180.0 | 1500.0     |
| 1608            | 2023-09-26 | 21:01:00  | 87          | Female | 55  | Electronics | 3        | 500.0          | 265.0 | 1500.0     |
| 199             | 2023-10-26 | 21:34:00  | 53          | Male   | 45  | Beauty      | 3        | 500.0          | 135.0 | 1500.0     |
| 1199            | 2023-12-16 | 17:46:00  | 110         | Male   | 45  | Beauty      | 3        | 500.0          | 190.0 | 1500.0     |
| 65              | 2022-12-11 | 20:03:00  | 84          | Male   | 51  | Electronics | 4        | 500.0          | 160.0 | 2000.0     |
| 1065            | 2023-10-24 | 15:16:00  | 76          | Male   | 51  | Electronics | 4        | 500.0          | 175.0 | 2000.0     |
| 580             | 2022-11-14 | 14:44:00  | 104         | Female | 31  | Clothing    | 3        | 500.0          | 200.0 | 1500.0     |
| 1580            | 2023-09-21 | 15:47:00  | 105         | Female | 31  | Clothing    | 3        | 500.0          | 250.0 | 1500.0     |
| 700             | 2022-09-01 | 15:07:00  | 61          | Male   | 36  | Electronics | 4        | 500.0          | 250.0 | 2000.0     |
| 828             | 2022-11-24 | 15:54:00  | 76          | Female | 33  | Electronics | 4        | 300.0          | 132.0 | 1200.0     |
| 1700            | 2023-09-27 | 16:10:00  | 87          | Male   | 36  | Electronics | 4        | 500.0          | 210.0 | 2000.0     |
| 1828            | 2022-10-14 | 14:14:00  | 99          | Female | 33  | Electronics | 4        | 300.0          | 165.0 | 1200.0     |
| 361             | 2022-09-12 | 16:37:00  | 112         | Female | 34  | Electronics | 4        | 300.0          | 81.0  | 1200.0     |
| 1361            | 2023-09-12 | 16:00:00  | 89          | Female | 34  | Electronics | 4        | 300.0          | 153.0 | 1200.0     |
| 139             | 2023-09-15 | 14:03:00  | 113         | Male   | 36  | Beauty      | 4        | 500.0          | 230.0 | 2000.0     |
| 1139            | 2023-12-21 | 14:23:00  | 87          | Male   | 36  | Beauty      | 4        | 500.0          | 230.0 | 2000.0     |
| 99              | 2023-11-19 | 15:12:00  | 71          | Female | 50  | Electronics | 4        | 300.0          | 132.0 | 1200.0     |
| 1099            | 2022-12-24 | 12:41:00  | 56          | Female | 50  | Electronics | 4        | 300.0          | 162.0 | 1200.0     |
| 757             | 2023-10-06 | 12:10:00  | 82          | Female | 43  | Electronics | 4        | 300.0          | 105.0 | 1200.0     |
| 1757            | 2023-09-29 | 16:42:00  | 50          | Female | 43  | Electronics | 4        | 300.0          | 132.0 | 1200.0     |
| 664             | 2022-09-03 | 16:52:00  | 109         | Female | 44  | Clothing    | 4        | 500.0          | 170.0 | 2000.0     |
| 1664            | 2023-12-12 | 16:44:00  | 99          | Female | 44  | Clothing    | 4        | 500.0          | 245.0 | 2000.0     |
| 805             | 2022-09-03 | 13:55:00  | 59          | Female | 30  | Beauty      | 3        | 500.0          | 155.0 | 1500.0     |
| 908             | 2022-10-30 | 14:47:00  | 64          | Male   | 46  | Beauty      | 4        | 300.0          | 81.0  | 1200.0     |
| 1805            | 2023-10-10 | 13:35:00  | 79          | Female | 30  | Beauty      | 3        | 500.0          | 225.0 | 1500.0     |
| 1908            | 2023-12-17 | 12:34:00  | 93          | Male   | 46  | Beauty      | 4        | 300.0          | 87.0  | 1200.0     |
| 211             | 2022-09-12 | 14:02:00  | 54          | Male   | 42  | Beauty      | 3        | 500.0          | 235.0 | 1500.0     |
| 1211            | 2023-11-22 | 14:59:00  | 82          | Male   | 42  | Beauty      | 3        | 500.0          | 235.0 | 1500.0     |

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
