# CAPSTONE-PROJECT

## Project Outline
- [Project Title](#project-title)
- [Project Overview For Sales Data](#project-overview-for-sales-data)
- [Project Overview For Customer Data](#project-overview-for-customer-data)
- [Column Description For Sales Data](#column-description-for-sales-data)
- [Column Description for Customer Data](#column-description-for-customer-data)
- [Data Sources](#data-sources)
- [Tools Used](#tools-used)
- [Data Cleaning and Preparations](#data-cleaning-and-preparations)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Data Visualization](#data-visualization)
- [Key Insights](#key-insights)
- [Limitation](#limitation)
- [Conclusion](#conclusion)


## Project Title
Sales Transaction and Customer Subsription Analysis

### Project Overview For Sales Data
This analysis aims to uncover insights in the sales data, focusing on sales trends, product performance, and customer distribution by region. By analysisng the various parameters in the data received, we seek to gather enough insight which then enables us to tell compelling stories around our data from the insight gotten and to know the best performance for our data.

### Project Overview For Customer Data
This analysis aims to uncover insights in customer subscription patterns and revenue. By analysisng the various parameters in the data received, we seek to gather enough insight which then enables us to tell compelling stories around our data from the insight gotten and to know the best performance for our data.

### Column Description For Sales Data
-  OrderID: A unique identifier for each order.
-  CustomerID: A unique identifier for each customer placing a particular order.
-  Product: The specific product purchased in each transaction.
-  Region: The geographical location (North, South, East and West) where the order was placed.
-  OrderDate: The date when the order was made.
-  Quantity: The number purchased for each product in an order.
-  UnitPrice: The price per unit of the product.
-  Total Sales: The total sales value for the order which is calculated as (Quantity * UnitPrice).

  ### Column Description for Customer Data
  - CustomerID: A unique Identifier for each customer.
  - CustomerName: Name of the customer.
  - Region: The geographical location (North, South, East and West) of the customer.
  - SubscriptionType: The type of subscription plan the customer opted for (e.g Basic, Premium and Standard).
  - SubscriptionStart: The start date of the customer's subscription.
  - SubscriptionEnd: The end date of the customer's subscription.
  - Canceled: This indicates if the subscription was canceled (TRUE or FALSE).
  - Revenue: Revenue generated from the customer's subscription.
  - Subscription Duration: The duration of the subscription period which is calculated as (SubscriotionEnd - SubscriptionStart).
    
### Data Sources
The main source of data used here are the Data Sales.csv and Customer.csv and this is an open source data that can be downloaded freely from an open source online such as Kaggle, FRED or any other data repository site.

### Tools Used:
- Microsoft Excel [Download Here](https://www.microsoft.com)
  1. for data cleaning
  2. for analysis
  3. for data visualization
     
- SQL-Structured Query Lanuage
  1. for Quering data
  2. for exploring data
       
- Power BI
  1. for data visualization
  2. for dashboard creation

  ### Data Cleaning and Preparations
  In the initial phase of data cleaning and preparations, we performed the following action;
  1. Data loading and Inspection
  2. Handling missing variables
  3. Data Cleaning and Formatting

  ### Exploratory Data Analysis
  EDA involved the exploratory of the data to anser some questions about data such as;
  
  #### For Sales Data
  1. What is the total sales for each product category?
  2. What is the number of sales transactions in each region?
  3. What is the highest selling product by total sales?
  4. What is the average of the total sales by product?
  5. What is the maximum quantity by product?
  6. What is the minimum quantity by product?
  7. What is the total revenue per product?
  8. Who are the 5 top customers by total puchase amount?
  9. What are the monthly sales total for the current year?
  10. The product with less sales by month.

  #### For Customer Data
  1. What is the total number of customers from each region?
  2. What is the most popular subscription type by the number of customers?
  3. What is the average subscription duration for all customers?
  4. How many customers caanceled their subscription within 6 months?
  5. How many customers have a subscription longer than 12 months?
  6. What is the total revenue by subscription type?
  7. What are the top 3 regions by subscription cancellations?
  8. How many active and canceled subscription is available?
  9. What region has the highest revenue?
  10. Who are the top 5 custonmers by revenue?
      
  ### Data Analysis
  This is where we include some basic lines of codes, queries or even some of the DAX expressions used during your analysis;

```SQL
Select * from [Capstone Sales Data]

---------Retrieve the Total Sales for each Product Category---------
Select PRODUCT,SUM(quantity * unitprice) as Total_Sales
From [Capstone Sales Data]
group by PRODUCT;


---------Find the Number of Sales Transactions in Each Region---------
Select REGION, COUNT(quantity * unitprice) as Total_Sales
from [Capstone Sales Data]
Group by REGION;


---------Find the highest selling Product by Total Sales Value-------
Select PRODUCT, SUM(quantity * unitprice) as 'Total_Sales'
from [Capstone Sales Data]
Group by PRODUCT
Order by Total_Sales DESC


---------Calculate Total Revenue Per Product-------------
Select PRODUCT, SUM(quantity * unitprice) as 'Total_Revenue'
from [Capstone Sales Data]
Group by PRODUCT;


--------Calculate Monthly Sales Totals for the Current Year------
Select MONTH(OrderDate) as Month,
SUM(quantity * unitprice) as 'Total_Sales'
from [Capstone Sales Data]
where YEAR(OrderDate)= 2024
Group by MONTH(OrderDate)
Order by MONTH;


----------Find the Top 5 Customers by Total Purchase Amount-----------
Select Customer_Id,
SUM(quantity * unitprice) as 'Total_Sales'
from [Capstone Sales Data]
Group by Customer_Id
Order by Total_Sales DESC


------------Calculate the Percentage of Total_Sales contributed by each Region
Select Region, SUM(quantity * unitprice) as Region_Sales,
SUM(quantity * unitprice) *1.0/ (Select SUM(quantity * unitprice) 
from [Capstone Sales Data]) * 100
as SalesPercentage
from [Capstone Sales Data]
Group by Region
Order by SalesPercentage DESC;

----------Identify the Product with no Sales in the Last Quarter------------
Select PRODUCT
from [Capstone Sales Data]
where PRODUCT NOT IN (Select DISTINCT PRODUCT from [Capstone Sales Data]
where OrderDate between '2024-07-01' and '2024-09-30');


-----------------------------------------------------------------------------------------
SELECT * FROM [LITA Capstone Customer Data] = CustomerData

Select Region, COUNT(CustomerID) as TotalCustomers
from [LITA Capstone Customer Data]
Group by Region;

--------Most Popular Subscription Type by Number of Customers-------
Select SubscriptionType, COUNT(CustomerID) as NumCustomers
From [LITA Capstone Customer Data]
Group by SubscriptionType
Order by NumCustomers DESC

 -------Customers who cancelled their Subscription within 6months------
 Select CustomerID,CustomerName,Canceled
 From [LITA Capstone Customer Data]
 where Canceled = 'TRUE' and MONTH(SubscriptionStart) between 1 and 6

 -------- Calculate the Average Subscription Duration for all Customers-------
 Select AVG(DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd)) as AVGDuration
 From [LITA Capstone Customer Data]

 ---------Find Customers with Subscriptions longer than 12 Months----------
 Select CustomerID,CustomerName, SubscriptionStart, SubscriptionEnd
 From [LITA Capstone Customer Data]
 where DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd) >365;

 ---------Calculate Total Revenue by Sibscription Type------
Select SubscriptionType, SUM(Revenue) as TotalRevenue
From [LITA Capstone Customer Data]
Group by SubscriptionType;

 ------Find the top 3 regions by Subscription Cancellations-------
Select Region, COUNT(CustomerID) as TotalCancellations
From [LITA Capstone Customer Data]
where Canceled = 'True' 
Group by Region
Order by TotalCancellations DESC;

 ------Find the Total Number of Active and Canceled Subscriptions------
Select Canceled, COUNT(CustomerID) as SubscriptionCount
From [LITA Capstone Customer Data]
Group by Canceled;
```
  
  ### Data Visualization

![Pivot for SalesData](https://github.com/user-attachments/assets/75bb9b32-073c-4347-8ac1-6f557c6f406d)


![Pivot for CustomerData](https://github.com/user-attachments/assets/88e6debe-622b-41f2-8cd3-74521add5ac8)


![Pivot Customer Data](https://github.com/user-attachments/assets/38121f7a-c18f-4525-ab6e-31bca05a37d3)


![SalesData](https://github.com/user-attachments/assets/96617d33-0bf6-48de-8462-80a4eb3ccde6)


![SalesData2](https://github.com/user-attachments/assets/140558c7-70fc-461d-94b2-fdddfabeb4a6)


![CustomerData](https://github.com/user-attachments/assets/1c8b341b-dcbe-40f8-832c-ed9183506ac4)


![CustomerData2](https://github.com/user-attachments/assets/84b6b84d-f40b-45d1-9533-f51636e1e537)


![BI for Sales Data](https://github.com/user-attachments/assets/50ef9661-4481-451a-b6b1-a3cf016b6563)


![BI for SalesData](https://github.com/user-attachments/assets/f6a71e4c-a727-4847-a101-9b2ab172f052)


![BI for CustomerData](https://github.com/user-attachments/assets/3895e228-1ac8-44f8-9f66-add2a1cea431)

## Key Insights
### Sales Overview
- **Total Sales**:    $2,101,090 was the total sales across all orders.
- **Revenue Trends**: Consistent growth, with peak sales in shoes.
- **Active vs. Canceled Subscriptions**: East Region is active, with a cancellation rate of 25.11%.

### Top-Performing Products
- **Best-Selling Products**: Product such as shoes, shirt, and Hat generated the highest revenue.
- **High-Demand Categories**: Basic Subscription showed substantial demand.

### Regional Breakdown
- **Regional Sales Distribution**:Southern Region led in sales, contributing 44% of total revenue.
- **Subscription Cancellations**: Highest in Southern Region, accounting for 14.99% of total cancellations.

## Limitation
-Granularity**: Weekly sales breakdowns were not available, which may obscure finer trends.


## Conclusion
The analysis highlights key areas for potential growth, such as expanding top-performing products and improving retention in regions with high cancellations. The dashboard can serve as a valuable tool for ongoing performance monitoring.

