# LITA_CAPSTONE_PROJECT
### Project Title: E Sales Analysis

### Project Overview
This data analysis projects uses Excel, SQL, and Power BI aims at generating insight from sales data, By analysing and visualizing sales data to gain insights into customer behavior, sales trends, and product performance. The analysis will help identify areas of improvement, optimize sales strategiesand making the best business decisions.
### Data Sources 
The Primary Source of Data used here a Sales Data .csv and close source data.

### Tools Used 
- Microsoft Excel for Data Cleaning , Analysis and visualization
- Sql  for querying of Data
- Power BI for visualization of Data
- GitHub for Portfolio Buiding
### Excel Files
- Sales Exploration: Initial data exploration using pivot tables.
- Sales Metrics: Calculations for average sales per product and total revenue by region.

  ### Sql Queries
  - Sales_queries: Queries for total sales by product category, number of sales transactions by region, highest-selling product, total revenue per product, monthly sales totals, top 5 customers, and percentage of total sales by region.

### Power BI Dashboards
- Sales Overview: Dashboard visualizing sales overview, top-performing products, and regional breakdowns

  ### Data Files
 - Sales_data: Sales data used for analysis.
### Instructions Given;
1.  Clone the repository.
2. Load the sales data into your SQL Server environment.
3. Run SQL queries to extract insights.
4. Open Excel files to view calculations and pivot tables.
5. Open Power BI dashboard files to visualize insights.

   ### Sql Queries Documentation
   CREATE DATABASE LITA_CAPSTONE_PROJECT_2

    ``` SQL
     SELECT FROM * [dbo].[Sales data]
    ```
``` SQL

--- 1. retrieve the total sales for each product category.---
SELECT[Product] , SUM([Sales]) AS TotalSales
FROM [dbo].[sales Data]
GROUP BY [Product]
```
``` SQL
--- 2. find the number of sales transactions in each region.
SELECT [Region], COUNT([OrderID]) AS NumOfTransactions
FROM [dbo].[sales Data]
GROUP BY [Region]
```
```SQL
-- 3. find the highest-selling product by total sales value.--
SELECT Top (1)[Product] , SUM([Sales]) AS TotalSales
FROM [dbo].[sales Data]
GROUP BY [Product]
ORDER BY TotalSales DESC
```

``` SQL
--- 4. calculate total revenue per product.---
SELECT[Product], SUM([Sales]) AS TotalRevenue
FROM [dbo].[sales Data]
GROUP BY [Product]
```

```SQL
--- 5. calculate monthly sales totals for the current year
SELECT Month([OrderDate]) AS Month,
    SUM([Sales]) AS MonthlySalesTotal
FROM[dbo].[sales Data]  WHERE YEAR([OrderDate]) = 2024
GROUP BY Month([OrderDate])
ORDER BY Month
```

```SQL 
-- 6. find the top 5 customers by total purchase amount.---
SELECT Top (5)[Customer_Id] ,
 SUM([Sales]) AS TotalPurchaseAmount FROM [dbo].[sales Data]
GROUP BY [Customer_Id]
ORDER BY TotalPurchaseAmount DESC
``` 

```SQL
-- 7. calculate the percentage of total sales contributed by each region.---
SELECT[Region] , SUM([Sales]) AS RegionTotalSales,
FORMAT(ROUND((SUM([Sales]) / CAST((SELECT SUM([Sales]) FROM [dbo].[sales Data]) AS DECIMAL(10,2)) * 100), 1), '0.#') 
AS PercentageOfTotalSales
FROM [dbo].[sales Data]
GROUP BY [Region]
ORDER BY PercentageOfTotalSales DESC
```
``` SQL
-- 8. identify products with no sales in the last quarter.---
SELECT [Product] FROM [dbo].[sales Data]
GROUP BY [Product]
HAVING SUM(CASE 
WHEN OrderDate BETWEEN '2024-06-01' AND '2024-08-31' 
THEN 1 ELSE 0 END) = 0
```
### visualization 

![sales data Excel](https://github.com/user-attachments/assets/161b484d-2ce3-46e5-88dc-1e43d4314e3f)
![sales data powe bi](https://github.com/user-attachments/assets/2b428bf2-11bf-4b76-b9b8-5951bfcc662e)
![power bi image](https://github.com/user-attachments/assets/2844c8e9-82d2-4d2f-9d4d-85604f2bb16f)
