
# Task Description — Excel Data Analysis Project

## Objective
The objective of this task is to clean, explore, and analyze a large retail sales dataset using Microsoft Excel.  
The task includes performing data cleaning, creating pivot tables, generating summary statistics, and designing a simple dashboard that provides insights on sales, profit, customers, and product categories.

## Dataset
The dataset used in this task is an Excel file named:
**store.xlsb.xlsx**

### Main Columns Identified
- **OrderID** – Unique ID for each order  
- **Order Date** – Date of order placement  
- **Ship Date** – Date order was shipped  
- **Ship Mode** – Type of shipping (e.g., Standard Class, First Class)  
- **Customer ID** – Unique identifier for each customer  
- **Customer Name** – Customer’s full name  
- **Segment** – Customer segment (e.g., Consumer, Corporate)  
- **City** – Customer location  
- **Region** – Sales region  
- **Product ID** – Product identifier  
- **Category** – Product category  
- **Sub-Category** – Product sub-category  
- **Product Name** – Detailed product description  
- **Sales** – Total sales amount  
- **Quantity** – Number of units sold  
- **Discount** – Discount applied  
- **Profit** – Profit earned  

> Note: The dataset contains an extremely large number of extra columns (far beyond Column Z). Only the relevant business columns were used in the analysis.

## Steps Performed
### 1. Data Cleaning
- Removed unnecessary blank columns.
- Standardized date formats (Order Date & Ship Date).
- Converted Sales, Profit, and Quantity to numerical format.
- Removed duplicated rows based on **OrderID + ProductID**.
- Fixed inconsistent category names where needed.

### 2. Data Exploration & Pivot Analysis
Created multiple PivotTables for:
- **Sales by Region**
- **Sales by Category & Sub-Category**
- **Profit by Product**
- **Top 10 Cities by Sales**
- **Sales trend over time (Monthly)**

### 3. Dashboard Creation
Designed an Excel dashboard including:
- Total Sales, Total Profit (KPIs)
- Sales Trend Chart (Line Chart)
- Sales by Category (Bar Chart)
- Top Cities by Sales (Bar/Column Chart)
- Profit by Region (Map/Bar Chart)

### 4. Deliverables
The task deliverables include:
- Cleaned Excel file containing tables, pivot tables, and dashboard
- Screenshots of the dashboard
- TaskDescription.md (this file)
- Reflection.md

## Tools Used
- Microsoft Excel (PivotTables, PivotCharts, Slicers, Formulas)
``

