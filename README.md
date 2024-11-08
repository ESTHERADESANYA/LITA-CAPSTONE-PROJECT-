# LITA-CAPSTONE-PROJECT-||CUSTOMER SEGMENTATION||
### PROJECT TITLE: CUSTOMER SEGMENTATION FOR SUBSCRIPTION SERVICE
- [PROJECT OUTLINE](###PROJECT-OUTLINE)
- [PROJECT OVERVIEW](###PROJECT-OVERVIEW)
- [PROJECT OBJECTIVES](###PROJECT-OBJECTIVES)
- [DATA TOOLS](###DATA-TOOLS)
- [Data PROFILE](###Data-PROFILE)
- [Data Collection](###Data-Collection)
- [METHODOLOGY](###METHODOLOGY)
- [SQL QUERIES](###SQL-QUERIES)
- [DATA VISUALIZATION](###DATA-VISUALIZATION)
- [RESULT](###RESULT)

### PROJECT OVERVIEW
```
This repository contains the documentation for the Lita Capstone Project, 
This project involves analyzing customer data for a subscription service
to identify segments and trends. The goal is to understand customer behavior
track subscription types, and identify key trends in cancellations and renewals.
```

### PROJECT OBJECTIVES:
```
Analyze customer data using pivot tables to
- find subscription patterns.
- Calculate the average subscription duration.
- Identify the most popular subscription types.
```

### DATA TOOLS:
```
Microsoft Excel: Data analysis, manipulation and visualization.(https://www.microsoft.com)[Download Here]
- SQL Server: Data storage and quering 
- Power BI: Data visualization and creating interesting reports.
- Gifthub for building portfolio
```

 ### Data PROFILE:
```
The Customer datasets includes the following fields:
 - CustomerID: Unique identifier for each transaction.
 - Customer Name: Name of a customer.
-  Region: geographical area or location associated with a customer
   (North,East,South,West)
 - Subscription Type: It involves different levels of service with customers
   choosing a plan (Basic, Premium,standard)
 - Subscription Start: The start date of the customers subscription.
 - Subscription End: The end date of customers Subscription.
 - Canceled: This indicates the status of a subscription, service that has been
   intentionally terminated before the end of its active period
 - Revenue: The total income earned typically from customers subscription 
 - Subscription Duration: This indicates the typical length of time that customers
   remain subscribed to a service before canceling, or switching payments
```

### Data Collection
```
The dataset for the analysis was provided by LITA Incubator Hub.`
```

### METHODOLOGY
### EXPLORATORY DATA ANALYSIS (EDA)
```
EDA is the first step in data analysis to understand its main characteristics
I worked on 33787 rows and 8 Columns
DATA MANIPULATION
1. Data Cleaning and Analysis on Excel:
   1. Data loading and inspection
   2. Checked for Null values and removed duplicates by highligting and using the remove duplicates features.
   3. Utilized Pivot tables to summarize data.
   4. Charts to visualize trends and pattern, Slicer for interactive filtering.
   FUNCTIONS
   Calculate the average subscription duration and identify the most popular subscription types.

2. Data Cleaning and Transformation on PowerBI: 
- Removed duplicates using remove Duplicates feature.
- Changed data types using the data type feature.
- Checked for data consistency using the column quality, column profile, and column distribution.
- Data visualization: created Power BI dashboard that visualizes key customer segments, cancellations, and subscription trends.
- I utilized slicers for interactive analysis.(e.g, charts, cards,tables).
```

### SQL QUERIES
```
- The cleaned data from Excel was saved as CSV files and then imported into the SQL Database System.
- I carried out my queries using DAX expressions, SQL Clauses and Data Query Language
- create database Customer_Data_Capstone
- --- 1 retrieve the total numbers from each region
select * from [dbo].[Customer_Dataset]
Select Region,
Count(CustomerID) as Totalcustomers from [dbo].[Customer_Dataset]
Group by region
Order by TotalCustomers DESC

- --- 2 find the most popular subscription type by the number of customers
select  subscriptiontype,
count(customerid) as numberofcustomers
from [dbo].[Customer_Dataset]
group by subscriptiontype
order by numberofcustomers desc 

- ----3 find customers who canceled their subscription within 6 months
Select CustomerID,CustomerName, SubscriptionType,
SubscriptionStart, SubscriptionEnd,
DATEDIFF(Month, SubscriptionStart,SubscriptionEnd) as SubscriptionDuration
From [dbo].[Customer_Dataset]
Where canceled = 1 and DATEDIFF(Month,SubscriptionStart,SubscriptionEnd)<=6
Order by SubscriptionDuration ASC

- ---- 4 Calculate the Average subscription duration for all customers
Select Avg(DATEDIFF(Month, SubscriptionStart,SubscriptionEnd)) 
as AverageSubscriptionDuration
From [dbo].[Customer_Dataset]
Where canceled = 1 
Select * From [dbo].[Customer_Dataset]

- --- 5 calculate the average subscriptionduration for all customer
Select CustomerID, CustomerName,SubscriptionType,
SubscriptionStart, SubscriptionEnd,
DATEDIFF(Month,SubscriptionStart,SubscriptionEnd) as SubscriptiononDuration
From [dbo].[Customer_Dataset]
where DATEDIFF(Month,SubscriptionStart,SubscriptionEnd) > 12 
Order by SubscriptiononDuration Desc


- ---6 calculate total revenue by subscription type
Select SubscriptionType,
Sum(Revenue )as Total_Revenue 
From [dbo].[Customer_Dataset]
Group by SubscriptionType
Order by Total_Revenue Desc

- ----7 FIND Top 3 categories byu subscription cancellation
Select Top 3 SubscriptionType,
Count(CustomerID)as CancellationsCount
From  [dbo].[Customer_Dataset]
Where Canceled = 1
Group by SubscriptionType
Order by CancellationsCount desc 

- --- 8 find the total number of active and canceled subscription
Select
Sum(Case When Canceled = 0 Then 1 Else 0 End) as ActiveSubscriptions,
Sum(Case When Canceled = 0 Then 1 Else 0 End) as CanceledSubscriptions
From [dbo].[Customer_Dataset]
```


  3. FUNCTIONS
   Calculate the average subscription duration and identify the most popular subscription types.

```

### DASHBOARD OVERVIEW
```
EXCEL VISUALIZATION
PIVOT TABLES
![20241105_152242](https://github.com/user-attachments/assets/675b18f9-636e-4b4a-9f36-94560eb62560)

CHARTS
![20241105_151511](https://github.com/user-attachments/assets/06b58c59-9f36-4842-b5c8-745881a7b7b3)
![20241105_151618](https://github.com/user-attachments/assets/434397f1-96ca-4b45-b29e-7c69d44d883f)


SQL RESULTS
![20241108_012325](https://github.com/user-attachments/assets/d47f9847-944a-4f29-b795-1587a56945fc)
![20241108_012451](https://github.com/user-attachments/assets/0f757757-2dab-4ec8-aa3c-4aca931448ff)
![20241108_012625](https://github.com/user-attachments/assets/3172aa9d-5dad-4d67-8df2-70c5a2663982)
![20241108_012724](https://github.com/user-attachments/assets/4bd07add-e6d8-4e84-89b3-0bfb61329647)
![20241108_012819](https://github.com/user-attachments/assets/a4e725ab-88bd-4201-8fe2-79f55a049c24)
![20241108_013323](https://github.com/user-attachments/assets/f2c6f3fb-5ed2-44d7-acce-8854ca6455f2)
![20241108_013524](https://github.com/user-attachments/assets/109c69cd-f753-4d02-9bd0-0e3bcda0f587)


### DATA ANALYSIS AND INSIGHT GENERATION
```
SUBSCRIPTION TYPE BY SUM OF REVENUE
Basic accounts for about 49.9% of the total revenue.
Premium and Standard each contribute about 25.0% to the total revenue

```
### CONCLUSION
```
``

###RECOMMENDATION
```
