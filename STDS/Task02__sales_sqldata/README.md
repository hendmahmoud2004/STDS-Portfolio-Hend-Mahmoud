
# 🧠 SQL Data Cleaning & Consolidation — AdventureWorksLT Sales

This project demonstrates end-to-end **SQL data preparation** on the AdventureWorksLT2022 sample database, followed by exporting analytics-ready data to Excel for pivot analysis and dashboarding.

We:
1) **Profiled** raw SalesLT tables  
2) **Built cleaned tables** (Address, Customer, CustomerAddress, Product, ProductCategory, ProductModel, ProductModelProductDescription, SalesOrderHeader, SalesOrderDetail)  
3) **Engineered date attributes** (day/month/year)  
4) **Merged** everything into a single wide table: **`Merged_SalesData`**  
5) **Exported to Excel** and created pivots/dashboards

> Source SQL: `Sales_SQLQuery1.sql`  
> Data export & pivots: `sales_sqldata (version 1).xlsb (1).xlsx` (contains sheets: **Pivots**, **Dashboard**, **sales_sqldata**) [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)2.xlsb%20(1).xlsx&action=default&mobileredirect=true)

---

## 📚 Tables Used (AdventureWorksLT2022)

- `SalesLT.Address`, `SalesLT.Customer`, `SalesLT.CustomerAddress`,  
  `SalesLT.Product`, `SalesLT.ProductCategory`, `SalesLT.ProductModel`,  
  `SalesLT.ProductModelProductDescription`, `SalesLT.SalesOrderHeader`, `SalesLT.SalesOrderDetail`  
  → Cleaned into `dbo.Clean_*` tables via `SELECT ... INTO` patterns in the script. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)

Key examples from the script:
- **Address → `Clean_Address`**: retains `AddressID, AddressLine1, City, StateProvince, CountryRegion, PostalCode` and null/duplicate checks. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)  
- **Customer → `Clean_Customer`**: retains `CustomerID, CompanyName, SalesPerson` and null/duplicate checks. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)  
- **Product → `Clean_Product`**: retains core pricing & category linkage; adds `SellStartDay/Month/Year` and (optionally) drops original date. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)  
- **SalesOrderHeader → `Clean_SalesOrderHeader`**: keeps business-critical header fields; derives `OrderDay/Month/Year`, `DueDay/Month/Year`, `ShipDay/Month/Year`, then drops original date columns after copying. [1](https://cimenofiaedu-my.sharepoint.com/personal/hend_mahmoud_ai_menofia_edu_eg/Documents/Microsoft%20Copilot%20Chat%20Files/Sales_SQLQuery1.sql)

---

## 🔗 Final Merge: `Merged_SalesData`

We left-joined all cleaned tables to produce the analytics dataset:

```sql
SELECT
  soh.SalesOrderID, soh.Status, soh.OnlineOrderFlag, soh.SalesOrderNumber, soh.PurchaseOrderNumber,
  soh.AccountNumber, c.CustomerID, c.CompanyName,
  a_ship.AddressLine1 AS ShipAddress, a_ship.City AS ShipCity, a_ship.StateProvince AS ShipState, a_ship.PostalCode AS ShipPostalCode,
  a_bill.AddressLine1 AS BillAddress, a_bill.City AS BillCity, a_bill.StateProvince AS BillState, a_bill.PostalCode AS BillPostalCode,
  sod.SalesOrderDetailID, sod.OrderQty, sod.UnitPrice, sod.UnitPriceDiscount, sod.LineTotal,
  p.ProductID, p.Name AS ProductName, p.StandardCost, p.ListPrice,
  pc.Name AS ProductCategory, pm.Name AS ProductModel, pmpd.Culture AS ProductDescription
INTO Merged_SalesData
FROM dbo.Clean_SalesOrderHeader AS soh
LEFT JOIN dbo.Clean_Customer AS c
  ON soh.CustomerID = c.CustomerID
LEFT JOIN dbo.Clean_CustomerAddress AS ca_ship
  ON soh.ShipToAddressID = ca_ship.AddressID AND soh.CustomerID = ca_ship.CustomerID
LEFT JOIN dbo.Clean_Address AS a_ship
  ON ca_ship.AddressID = a_ship.AddressID
LEFT JOIN dbo.Clean_CustomerAddress AS ca_bill
  ON soh.BillToAddressID = ca_bill.AddressID AND soh.CustomerID = ca_bill.CustomerID
LEFT JOIN dbo.Clean_Address AS a_bill
  ON ca_bill.AddressID = a_bill.AddressID
LEFT JOIN dbo.Clean_SalesOrderDetail AS sod
  ON soh.SalesOrderID = sod.SalesOrderID
LEFT JOIN dbo.Clean_Product AS p
  ON sod.ProductID = p.ProductID
LEFT JOIN dbo.Clean_ProductCategory AS pc
  ON p.ProductCategoryID = pc.ProductCategoryID
LEFT JOIN dbo.Clean_ProductModel AS pm
  ON p.ProductModelID = pm.ProductModelID
LEFT JOIN dbo.Clean_ProductModelProductDescription AS pmpd
  ON p.ProductModelID = pmpd.ProductModelID;
```
---
# 📊 Sales Analytics & Excel Deliverables

This phase of the project focuses on transforming the cleaned SQL output into a professional reporting tool using Microsoft Excel.

## 📈 Excel Workbook Structure
The final report consists of three specialized sheets:
* **sales_sqldata Sheet:** The "Source of Truth" — a clean, flat dataset exported from SQL, fully prepared for analysis.
* **Pivots Sheet:** Contains dynamic summaries, including **Net Sales by Category** and key **Order Metrics** to identify business trends.
* **Dashboard Sheet:** A high-level visual interface featuring **KPIs** and interactive **Slicers** for real-time data filtering.



---

## 🛠 Tech Stack & Skills Applied

| Tool | Expertise Demonstrated |
| :--- | :--- |
| **SQL Server (T-SQL)** | Data Profiling, Cleaning, `SELECT INTO`, `ALTER TABLE`, and managing Complex Joins. |
| **Microsoft Excel** | Advanced Pivot Tables, Calculated Measures, Data Visualization, and Dashboard UI/UX design. |

---

## 📦 Project Deliverables
* 📜 **[Sales_SQLQuery1.sql](./Sales_SQLQuery1.sql)** — Full SQL pipeline script.
* 📊 **[Sales_Analytics_Report.xlsx](./sales_sqldata%20(version%201).xlsx)** — Final Excel Dashboard.
* 🖼️ **![Sales Dashboard Preview](Dashboard_Screenshot.png)** _ Dashboard Preview
---

## 📝 Student Reflection

### 💡 What I Learned
Through this task, I mastered the process of **Data Consolidation**. I learned that data is rarely ready for analysis in its raw form and requires a structured SQL pipeline to handle nulls and relational joins before it can be useful for business intelligence.

### ⚠️ Challenges Faced
The biggest challenge was managing the **Multiple Joins** between addresses (Shipping vs. Billing). I had to ensure that the correct `AddressID` was mapped to the correct record without creating duplicate rows, which required careful use of `LEFT JOIN`.

### 🚀 Improvements from Previous Tasks
Compared to previous exercises, I improved my **documentation skills** and learned how to transition data smoothly from a technical environment (SQL Server) to a business-friendly environment (Excel Dashboards).

