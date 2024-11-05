# LITA-PROJECT-2
Customer Subscription Behavior Analysis for MLITAFLIX Subscription Service

## Project Title: MLITAFLIX Sales Data Analysis

### Project Overview

This project involves analyzing customer data for a subscription service to identify segments and trends. The goal is to understand customer behavior, track subscription types, and identify key trends in cancellations and renewals. The final deliverable is a Power BI dashboard that presents THE analysis.


#### Outline
1. [Background and Objective](#background-and-objective)
2. [Data Sources and tools used](#data-sources-and-tools-used)
3. [Exploratory Data Analysis](#exploratory-data-analysis)
4. [Key Insights and Interpretation](#key-insights-and-interpretation)
5. [Code and Queries preview](#code-and-queries-preview)
6. [Data Visuals](#data-visuals)
7. [PowerBI Dashboard](#powerbi-dashboard)
8. [Results](#results)
9. Conclusion(#conclusion)

### Background and Objective

### Data Sources and tools used
Data Source: Data was gotten from the incubator hub- Ladies in tech Africa (LITA) Capstone Project in the form of an excel sheet
Tools used include;
- Microsoft Excel: For Data cleaning, initial data exploration and analysis
- SQL server management studio: Used for complex data querying to find out details of the data
- PowerBI Desktop: For building an interactive dashboard to present the key insights

### Exploratory Data Analysis
- Data Description; The unique columns contained in the excel sheet
  1. CustomerID - Unique identifier for each customer
  2. Region - geographical location of customer
  3. SubscriptionType - Type of MLITAFLIX subscription plan (basic,standard,premium)
  4. SubscriptionStard and End - Time Frame for the subscription start and end
  5. Canceled - shows if it an active or inactive subscription
  6. Revenue - Revenue generated from each customer's subscription

 - Methodology
   1. Initial data exploration in excel to understand the dataset
   2. Data cleaning; Removed duplicates
   3. Data summarization with Pivot tables to find key metrics and calculations
   4. import flat file to SQL
   5. SQL queries for more detailed analysis
   6. PowerBI creation of dashboard

   ### Key Insights and Interpretation
- Total revenue generated in the years
- Most popular subscription type
- Average duration of customer subscription
- Cancellation and renewal rates
- factors contributing to subscription cancellation


### Code and Queries Preview
---
     SQL QUERIES
1. Total Numbers of Customers from Region
   
Select Region, Count(CustomerID) as [Total Customers]
from LitaCustomerData Group by Region Order by 2 DESC

2. Most popular subscription type by number of customers
   
Select TOP 1 SubscriptionType, Count(CustomerID) as Customers 
From LitaCustomerData Group by SubscriptionType

Select SubscriptionType, Count(CustomerID) as Customers 
From LitaCustomerData Group by SubscriptionType

3. Customers who cancelled their subscription within 6months
   
 Select * from LitaCustomerData Where Canceled = 'True' 
AND DATEDIFF(Month,SubscriptionStart,SubscriptionEnd) <= 6

-----Alternative Query
Select * from LitaCustomerData where Canceled = 'True'
AND SubscriptionEnd <= DATEADD(Month,6,Subscriptionstart)

-----To check for the general subscription length in months
SELECT CustomerID, CustomerName, Region, SubscriptionType, SubscriptionStart, SubscriptionEnd, 
DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) AS SubscriptionDuration
FROM LitaCustomerData
WHERE Canceled = 'TRUE'

4. Average duration for subscription
   
Select AVG(Datediff(Month, SubscriptionStart,SubscriptionEnd)) As AverageDuration From LitaCustomerData

5. Customers with subscription longer than 12months
   
Select CustomerId,CustomerName,Region From LitaCustomerData Where DATEDIFF(MONTH,Subscriptionstart,SubscriptionEnd) >12

---No customer stayed longer than !2months

6. Total revenue by subscription type
   
Select Subscriptiontype, Sum(revenue) As TotalRevenue From LitaCustomerData
Group by Subscriptiontype Order by TotalRevenue DESC

7. Top 3 regions by subscription cancellation

 Select Top 3 Region, Count (Canceled) AS SubCancellation FROM LitaCustomerData
  Where Canceled = 'True' 
  Group by Region

8. Total number of canceled and active subscriptions
   
```Select Count(Canceled) as INACTIVESUB From LitaCustomerData
where Canceled = 'True' ```

```Select Count(Canceled) as ACTIVESUB From LitaCustomerData
where Canceled = 'FALSE' ```


---

### Data Visuals
![image](https://github.com/user-attachments/assets/1e7772b8-c4d6-4028-a504-ca012f238255)
![project 2 excel](https://github.com/user-attachments/assets/a636ce58-31ba-4591-b3c6-105d014f0f50)
![sql p23](https://github.com/user-attachments/assets/85e82515-d69b-4e15-b4e9-6ea52fea67ae)
![sql p22](https://github.com/user-attachments/assets/af40df26-7719-476f-958f-130b964b999b)
![sql p21](https://github.com/user-attachments/assets/8c1c2e60-4cb4-45c3-a263-60f44db0cad5)
![sql p2](https://github.com/user-attachments/assets/14c39286-dd37-47de-a942-d22d87bdd743)
![project 2excel cont](https://github.com/user-attachments/assets/a475dada-8bf1-47d8-a66b-10afe4106d76)


### PowerBI Dashboard

![dashboard project 2](https://github.com/user-attachments/assets/a35955a0-f6e9-4c7a-b9cd-afe1daf7b12f)

### Results




      

