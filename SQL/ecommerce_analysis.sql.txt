-- ==========================================================
-- E-COMMERCE SALES PERFORMANCE ANALYTICS - SQL QUERIES
-- Database: ECommerceDB
-- Table: SalesData
-- ==========================================================

-- 1. OVERALL BUSINESS KPI SUMMARY
-- Calculates total orders, total revenue, total profit, and overall profit margin %

SELECT * 
FROM [dbo].[SalesData]

SELECT 
COUNT (Order_ID) AS Total_Orders, 
ROUND (SUM(Sales), 2) AS Total_Revenue,
ROUND (SUM(Profit), 2) AS Total_Profit,
ROUND (SUM(Profit) / SUM (Sales) * 100, 2) AS Overall_Profit_Margin
FROM SalesData 

-- 2. SALES & PROFIT PERFORMANCE BY REGION
-- Ranks geographic regions by sales performance

SELECT Region,
COUNT(Order_ID) AS Total_Orders,
ROUND(SUM(Sales), 2) AS Region_Revenue,
ROUND(SUM(Profit), 2) AS Region_Profit
FROM SalesData
GROUP BY Region
ORDER BY Region_Revenue DESC

-- 3. PRODUCT CATEGORY & SUB-CATEGORY BREAKDOWN
-- Identifies top-performing product categories

SELECT Category,Sub_Category,
SUM(Quantity) AS Total_Units_Sold,
ROUND(SUM(Sales), 2) AS Total_Sales,
ROUND(SUM(Profit), 2) AS Total_Profit
FROM SalesData
GROUP BY Category, Sub_Category
ORDER BY Total_Sales DESC

-- 4. ADVANCED WINDOW FUNCTION: TOP 5 HIGHEST VALUE ORDERS PER REGION
-- Uses ROW_NUMBER() OVER (PARTITION BY ...) to rank orders within each region

WITH RankedOrders AS (
SELECT Region, Order_ID, Customer_ID, Sales, Profit,
ROW_NUMBER() OVER (PARTITION BY Region ORDER BY Sales DESC) AS Order_Rank
FROM SalesData
)
SELECT Region, Order_ID, Customer_ID, Sales, Profit
FROM RankedOrders
WHERE Order_Rank <= 5