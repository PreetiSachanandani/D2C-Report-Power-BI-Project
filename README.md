# D2C-Report-Power-BI-Project
This synthetic dataset simulates the operations of a Direct-to-Consumer (D2C) skincare e-commerce business.We shall build and implement a data solution using Microsoft Power BI as the client is already using Microsoft technology.


GOAL:
The project aims at building and implementing a data solution that includes:
•	Power BI Report ( Customer Analytics, Revenue Analytics, Product Profitability Analysis, Customer Lifetime Value (CLV), RFM Segmentation, Return Analysis)
•	E-Commerce Business Intelligence
•	Data Cleaning & Modeling Practice


STEPS:
Layer	Tool\
Data Source	Excel / CSV\
Data Ingestion	Power Query / Python\
Data Engineering	SQL\
Semantic Layer	Power BI\
BI Layer	Power BI Dashboard\
AI Layer	Python forecasting\


DATA PIPELINE
Step 1 — Data Ingestion
In this step, we shall see how raw operational data is ingested into the analytics platform.
Tool: Power Query ingestion
All the files are imported in Power BI using Get Data tab.

Step 2 — Data Engineering 
Once the raw data is ingested in the system the first step is creating relationships between the Fact and Dimension tables. Most of the relationships are formed automatically. 

TRANSFORMATIONS: 
1.	Lets first create a separate Date Table , add columns for time intelligence functions to work properly, such as Date, Day, Quarter, Month, Year and ensure to “Mark as a date table”.
2.	Checking for Date column in all the data files and simplify them to Short Format and convert them so that they can form relationship with Date Table.
3.	For all the data tables, turn on Column Quality, Column Distribution and Column Profile, skim through for each table for data discrepancies.
4.	Table: Orders have Null Values in “Delivered_Date” column for Cancelled orders and In Transit orders. Here, the null values are indicative of Not Applicable and are not missing per se. All the remaining tables show no duplicate entries and no null values.
5.	Merge Queries: Calculate Profit and create a new column in Orders table, bringing in Product ID from Order_items table and Cost from Products table. Create new column: Profit: Gross Amount – Cost
6.	For the Cancelled orders, the profit appears as Loss, hence Profit is replaced with Zero for Cancelled and In Transit orders by creating a conditional column.
7.	Handling 1 duplicate entry found in Fact Table: Remove Duplicates under Remove Rows applied to Fact_orders table. 

Feature Engineering:
1. Delivery_Days = Delivery Date - Ship Date
2. Profit = Gross Amount - Cost
3. Discount Impact %
4. CLV

Data Validation Rules
Example:
quantity > 0
sales > cost
delivery_days < 30

Step 3 — Data Modelling
A star schema works best for this dataset as it ensures scalability and fast query performance:
Fact Table:
•	Orders 
Dimension Tables:
•	Customers 
•	Products 
•	Date 
•	Order_items
•	Returns 
•	Reviews

Step 4 — Semantic Layer 
I have created following standardized metrics that shall provide meaning to the model:
Total Sales	Customer Lifetime Value
Total Profit	RFM
Profit Margin	Average Rating
Step 4 — BI Dashboard layer

Sheet1: Introduction and Navigation

Sheet2: Executive Overview: Sales Performance
KPIs include:
•	Revenue 
•	Profit 
•	Orders 
•	Customer count
•	Profit Margin
•	Returns rate
Visuals include:
•	Month on Month Sales
•	Sales by Payment method: helps in ascertaining preferred payment method
•	Sales Channel contribution to Sales and Profit
•	Sales by Order Status 

Sheet3: Customer Analytics and CLV
Visuals include:
•	Gender-wise contribution to Sales 
•	Customers per Acquisition channel
•	Top 20 customers with the help of CLV
•	New Customers per Month over years

Sheet4: RFM SEGMENTATION 
Visuals include:
•	Customer Segmentation 
•	Sales by Customer Segmentation category

Sheet5: Product Profitability 
KPIs include:
•	Total Profit
•	Total Sales
•	Profit Margin
Visuals include:
•	Total Sales by Key Ingredient  
•	Category-wise Profit 
•	Table showing Product Name, Profit Margin, Quantity sold and Cost Price


Sheet6: Customer Experience and Return 
KPIs include:
•	Return %
•	Average Rating
Visuals include:
•	Most Returned Products chart
•	Refund Status for Returned Products
•	Rating by Customers
•	Reasons for return
•	Returns per Month (Trend)

