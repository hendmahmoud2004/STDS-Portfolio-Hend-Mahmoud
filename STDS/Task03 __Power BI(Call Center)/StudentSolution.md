# Student Solution: Call Center Power BI Dashboard

## 1. Data Understanding & Preparation
I started by exploring the Call Center dataset to understand its structure and key fields
such as call timestamp, call reason, channel, sentiment, and call duration.

Basic data cleaning was performed by:
- Verifying data types
- Ensuring date and numeric columns were correctly formatted
- Reviewing missing values

---

## 2. Date Table Creation
To enable accurate time-based analysis, I created a separate Date Table using DAX:

```DAX
Date Table =
CALENDAR(
    MIN('Call Center_Call Center'[Call Timestamp]),
    MAX('Call Center_Call Center'[Call Timestamp])
)
```
Additional columns were added to the Date Table to enhance chronological sorting and visualization:
* **Day:** (Day name for weekly analysis).
* **Day No:** (Numeric order to ensure "Monday" comes before "Tuesday").
* **Month & Year:** For long-term trend tracking.

### 2. Data Modeling
A **One-to-Many (1:N)** relationship was established to enable precise filtering:
* **Date Table [Date]** ↔ **Call Center Data [Call Timestamp]**
* *The Date Table acts as the primary filter for all time-related visuals.*



---

## 🔢 DAX Measures
Advanced DAX measures were developed to calculate Key Performance Indicators (KPIs):

```dax
-- 1. Total Calls
Total Calls = COUNTROWS('Call Center_Call Center')

-- 2. Total Call Duration (min)
Total Call Duration (min) = SUM('Call Center_Call Center'[Total Call Duration (min)])

-- 3. Average Call Duration
Avg Call Duration (min) = DIVIDE([Total Call Duration (min)], [Total Calls], 0)

-- 4. Response Time % (SLA Compliance)
Response time % = 
DIVIDE(
    CALCULATE(
        [Total Calls],
        'Call Center_Call Center'[Response Time] = "Within SLA" 
        || 'Call Center_Call Center'[Response Time] = "Above SLA"
    ),
    [Total Calls], 0
)
```

## 📊 Dashboard Design & Insights

The dashboard was designed with a focus on **Clarity, Consistency, and Professionalism**, ensuring that key metrics are visible at a glance.

### 🎨 Design Elements
* **KPI Cards:** Providing a high-level overview of essential metrics for quick decision-making.
* **Call Distribution Analysis:** Interactive Bar Charts displaying call volumes by:
    * Day of the week.
    * Call Reason.
    * Communication Channel.
    * Call Center location.
* **Sentiment Analysis:** Visual representation of customer satisfaction levels.
* **Operational Detail:** A comprehensive table for tracking individual call records.
* **Interactive Slicers:** Dynamic filtering by **Date, City, and Channel** for deeper data exploration.

---

### 🔍 Key Insights & Findings
Based on the data analysis, the following observations were made:
* **Top Reason:** Billing Questions represent the most common reason for customer inquiries.
* **Channel Preference:** The **Chatbot** and **Call Center** channels handle the vast majority of incoming calls.
* **SLA Compliance:** Overall service level agreement (SLA) compliance is approximately **75%**.
* **Volume Trends:** Call volume is not static; it fluctuates significantly depending on the **day of the week**.

---

## 📦 Project Deliverables
All project-related files are included in this folder:

| File Type | Description | Link |
| :--- | :--- | :--- |
| **Power BI Report** | Full interactive dashboard file (`.pbix`) | [Download Here](./Call_Center_Analysis.pbix.pbix) |
| **Dataset** | Raw call center records (`.csv`) | [View Data](./Call_Center_Data.csv.csv) |
| **Screenshots** | High-resolution dashboard previews | [View Folder](./Screenshots/) |

---
