# Task Description — SQL Cleaning & Analytics Dataset

## Objective
Prepare an **analytics-ready sales dataset** by cleaning multiple AdventureWorksLT2022 tables, engineering date attributes, and consolidating them into a single wide table (**Merged_SalesData**) suitable for BI tools and Excel pivots. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)

## Source System
- Database: **AdventureWorksLT2022** (SalesLT schema)  
- Tables: Address, Customer, CustomerAddress, Product, ProductCategory, ProductModel, ProductModelProductDescription, SalesOrderHeader, SalesOrderDetail. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)

## Data Preparation Steps
1. **Column & type profiling** via `INFORMATION_SCHEMA.COLUMNS`. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)  
2. **Row counts** and **data previews** for each table. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)  
3. **Clean tables (`dbo.Clean_*`)** created using `SELECT ... INTO` with essential columns only:
   - `Clean_Address`, `Clean_Customer`, `Clean_CustomerAddress`, `Clean_Product`,  
     `Clean_ProductCategory`, `Clean_ProductModel`, `Clean_ProductModelProductDescription`,  
     `Clean_SalesOrderHeader`, `Clean_SalesOrderDetail`. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)
4. **Null checks** and **duplicate checks** on each `Clean_*` table (SUM(CASE WHEN ...), GROUP BY HAVING COUNT(*)>1). [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)
5. **Date engineering**:
   - `Clean_Product`: `SellStartDay/Month/Year` and (optional) drop original date. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)
   - `Clean_SalesOrderHeader`: add `OrderDay/Month/Year`, `DueDay/Month/Year`, `ShipDay/Month/Year` and drop original date columns after copying. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)
6. **Merge** all cleaned tables into **`Merged_SalesData`** using LEFT JOINs across header, detail, customer, addresses, product/category/model/description. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)

## Output & Analysis
- **Merged_SalesData** exported to Excel → `sales_sqldata (version 1).xlsb (1).xlsx`. 2.xlsb%20(1).xlsx&action=default&mobileredirect=true)
- Excel contains:
  - `sales_sqldata` sheet (dataset with **Order, Customer, Location, Product, Category, Pricing, Net Sales**). 2.xlsb%20(1).xlsx&action=default&mobileredirect=true)
  - `Pivots` sheet (e.g., **Sum of Net Sales**, **Count of SalesOrderID**, **Avg Order Value**, **Total Orders** by category/city/region). 2.xlsb%20(1).xlsx&action=default&mobileredirect=true)
  - `Dashboard` sheet (final visuals). 2.xlsb%20(1).xlsx&action=default&mobileredirect=true)

## Deliverables
- SQL script: `Sales_SQLQuery1.sql` (cleaning + merging). [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)  
- Exported dataset: `Sales_Export.csv` (optional).  
- Excel analysis: `sales_sqldata (version 1).xlsb (1).xlsx` (pivots + dashboard). 2.xlsb%20(1).xlsx&action=default&mobileredirect=true)

## Acceptance Criteria
- Clean tables exist with correct keys and minimal nulls/duplicates. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)  
- `Merged_SalesData` includes header, detail, customer, address, product & category fields. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)  
- Excel shows correct aggregations for **Net Sales**, order counts, and category/location breakdowns. 2.xlsb%20(1).xlsx&action=default&mobileredirect=true)
