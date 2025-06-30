# Telecom Churn Analysis Dashboard


##  Project Overview

This project presents an interactive *Power BI dashboard* for analyzing customer churn in a telecommunications company. The dashboard provides insights into churn reasons, customer demographics, subscription types, and account behaviors, helping stakeholders make data-driven decisions to reduce churn.

##  Dataset Summary

The dataset consists of *6,687 total customers, of which **1,796 have churned, resulting in a churn rate of **26.86%*. The data includes:
- Contract type
- Churn reason
- International plan usage
- Total charges
- Customer demographics (gender, age)
- Account length

##  Dashboard Features

The dashboard is broken down into the following sections:

-  *Top KPIs*:  
  - Total Customers: 6,687  
  - Churned Customers: 1,796  
  - Intl Active Churn Rate: 882  
  - Intl Plan Churn Rate: 162  
  - Churn Rate: 26.86%  
  - Total Charges: 7M

-  *Visuals*:  
  - *Churn Category Bar Chart*  
  - *Churn by Unlimited Data Plan*  
  - *Churn Reason Breakdown*  
  - *Customer Table* with contract and churn info  
  - *Average Age of Churned Customers*  
  - *Churn % by Account Length*

-  *Filters*:  
  - Gender slicer (Female, Male, Prefer not to say)  
  - Churn category segmentation  
  - Contract category toggle

##  Insights & Highlights

- *Competitor-related churn is highest*, followed by dissatisfaction and attitude issues.
- Majority of churned customers are on *month-to-month contracts*.
- Churn is more common among customers with *shorter account lengths*.
- Customers using *unlimited data* show higher churn behavior.

## DAX Measures Used

Here are some key *DAX* calculations used in the dashboard:

```DAX
-- Total Churners
Total Churners = CALCULATE(COUNTROWS(Customers), Customers[Churn] = "Yes")

-- Churn Percentage
Churn Percentage = DIVIDE([Total Churners], [Total Customers], 0)

-- Total Customers
Total Customers = COUNTROWS(Customers)

-- Intl Active-Churn Rate
Intl Active-Churn = CALCULATE(COUNTROWS(Customers), 
                               Customers[Churn] = "Yes", 
                               Customers[Int'l Plan] = "Yes")

-- Total Charges
Total Charges = SUM(Customers[TotalCharges])

-- Churn by Gender
Female Churners = CALCULATE([Total Churners], Customers[Gender] = "Female")
