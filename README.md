# LITA_CAPSTONE_PROJECT1
My first project while learning Data Analysis with The Incubator Hub
##LITA_CAPSTONE_PROJECT1
### Project Title: SALES DATA ANALYSIS

- Project Overview
- Tools Used

### PROJECT OVERVIEW
This project contains data analysis projects using tools like Excel,SQL and Power BI to generate insight into the sales performance of the sales data. The objective of this project is to analyze and visualize various parameters in the sales data. This analysis will help in gathering enough insights to identify areas of improvement,also to make reasonable business decisions and to know the best performance from the sales data.

### TOOLS USED:
- MICROSOFT EXCEL: For data cleaning, analysis 
- SQL: Structured Query Language for querying of data
- POWER BI: For Visualization
- GITHUB: For Portfolio Building

### Project Structure:
Excel: Contains Excel files for data exploration and calculation.
SQL: Contains SQL queries for data analysis.
Power BI: Contains Power BI dashboard files(Data and Visualization).

### Excel Files:
Sales Exploration: Initial data exploration using pivot tables.
Sales Metrics: Calculations for average sales per product and total revenue by region.



### Power BI Dashboards:
Sales Overview: 
- Dashboard visualizing sales overview
- Top-performing products
- Regional breakdowns.
  
### Instructions
- Clone the repository.
- Load the sales data into your SQL Server environment.
- Run SQL queries to extract insights.
- Open Excel files to view calculations and pivot tables.
- Open Power BI dashboard files to visualize insights.
### Data Analysis Using SQL
#### retrieve the total sales for each product category
``` 
SELECT Product, SUM(Sales) AS Total_sales
FROM [dbo].[LITA_Capstone_Project_Dataset]
GROUP BY Product
```
#### find the number of sales transactions in each region.
```
SELECT Region, COUNT(OrderID) AS No_Of_Transactions
FROM [dbo].[LITA_Capstone_Project_Dataset]
GROUP BY Region
```

#### find the highest-selling product by total sales value
```
SELECT Top (1) Product, SUM(Sales) AS Total_Sales
FROM [dbo].[LITA_Capstone_Project_Dataset]
GROUP BY Product
ORDER BY Total_Sales DESC
```
#### calculate total revenue per product.
```
SELECT Product, SUM(Revenue) AS Total_Revenue
FROM [dbo].[LITA_Capstone_Project_Dataset]
GROUP BY Product
```
#### calculate monthly sales totals for the current year
```
SELECT Month(OrderDate) AS Month,
SUM(Sales) AS Monthly_Sales_Total
FROM [dbo].[LITA_Capstone_Project_Dataset] WHERE YEAR(OrderDate) = 2024
GROUP BY Month(OrderDate)
ORDER BY Month
```
#### find the top 5 customers by total purchase amount.
```
SELECT Top (5) Customer_Id,
 SUM(Sales) AS Total_Purchase_Amount FROM [dbo].[LITA_Capstone_Project_Dataset]
GROUP BY Customer_Id
ORDER BY Total_Purchase_Amount DESC
```
#### calculate the percentage of total sales contributed by each region
```
SELECT Region, SUM(Sales) AS Region_Total_Sales,
FORMAT(ROUND((SUM(Sales) / CAST((SELECT SUM(Sales) FROM [dbo].[LITA_Capstone_Project_Dataset] ) AS DECIMAL(10,2)) * 100), 1), '0.#') 
AS Percentage_Of_Total_Sales
FROM [dbo].[LITA_Capstone_Project_Dataset]
GROUP BY Region
ORDER BY Percentage_Of_Total_Sales DESC
```
#### identify products with no sales in the last quarter
```
SELECT Product FROM [dbo].[LITA_Capstone_Project_Dataset]
GROUP BY Product
HAVING SUM(CASE 
WHEN OrderDate BETWEEN '2024-06-01' AND '2024-08-31' 
THEN 1 ELSE 0 END) = 0
```

`
