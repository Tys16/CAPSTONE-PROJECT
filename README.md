# CAPSTONE-PROJECT

## Project Title: Sales Transaction and Customer Subsription Analysis

### Project Overview For Sales Data: This analysis aims to uncover insights in the sales data, focusing on sales trends, product performance, and customer distribution by region. By analysisng the various parameters in the data received, we seek to gather enough insight which then enables us to tell compelling stories around our data from the insight gotten and to know the best performance for our data.

### Project Overview For Customer Data: This analysis aims to uncover insights in customer subscription patterns and revenue. By analysisng the various parameters in the data received, we seek to gather enough insight which then enables us to tell compelling stories around our data from the insight gotten and to know the best performance for our data.

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
    
### Data Sources: The main source of data used here are the Data Sales.csv and Customer.csv and this is an open source data that can be downloaded freely from an open source online such as Kaggle, FRED or any other data repository site.

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
  This is where we include some basic lines of codes, queries or even some of the DAX expressions ued during your analysis;
  
  Select * From Table Name = SalesData

  Select * From Table Name = CustomerData

  ### Data Visualization

 
  
