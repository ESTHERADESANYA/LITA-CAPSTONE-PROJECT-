# LITA-CAPSTONE-PROJECT-||
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
- Analyze customer data using pivot tables to
  find subscription patterns.
- Calculate the average subscription duration.
= Identify the most popular subscription types.
```

### DATA TOOLS:
```
Microsoft Excel: Data analysis, manipulation and visualization. [Download Here](https://www.microsoft.com)
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
``

### METHODOLOGY:
```
EXPLORATORY DATA ANALYSIS (EDA)
EDA is the first step in data analysis to understand its main characteristics
I worked on 33787 rows and 8 Columns
1. Data Cleaning and Analysis on Excel:
   1. Data loading and inspection
   2. Checked for Null values and removed duplicates by highligting and using the remove duplicates features.
   3. Utilized Pivot tables to summarize data.
   4. Charts to visualize trends and pattern, Slicer for interactive filtering.
   FUNCTIONS
   Calculate the average subscription duration and identify the most popular subscription types.

### SQL QUERIES
```
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


  
2. Data Cleaning and Transformation on PowerBI: 
- Used power query editor to clean and transform data.
- Removed duplicates using remove Duplicates feature.
- Changed data types using the data type feature.
- Checked for data consistency using the column quality, column profile, and column distribution.
- Data visualization: created Power BI dashboard that visualizes key customer segments, cancellations, and subscription trends. I utilized slicers for interactive analysis.
(e.g, charts, cards,tables).
  3. FUNCTIONS
   Calculate the average subscription duration and identify the most popular subscription types.

```

### DATA VISUALIZATION
![customer segment data (2)](https://github.com/user-attachments/assets/0db78788-48ae-4dc2-83f0-bb1e2250e3f0)
![customer segment data](https://github.com/user-attachments/assets/fce289b4-3368-4c17-8536-752686eed4f1)
![20241105_152310](https://github.com/user-attachments/assets/83332d68-2252-4f9e-ae0a-88abd6a8aea9)

### RESULTS
SUBSCRIPTION TYPE BY SUM OF REVENUE
Basic accounts for about 49.9% of the total revenue.
Premium and Standard each contribute about 25.0% to the total revenue

