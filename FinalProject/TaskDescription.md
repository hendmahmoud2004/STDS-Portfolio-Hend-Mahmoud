
# Final – Design Thinking for Data Scientist: GreenStream Energy

## Case Study Background
GreenStream Energy is a smart-utility provider collecting electricity usage data from 50,000 households via smart meters. The data is currently “dark data”—stored but not transformed into actionable insights.

**Strategic goals:**
- Identify peak energy consumption periods
- Detect abnormal or faulty smart meters
- Prepare data for future predictive analytics and forecasting

**Solution approach:** Design a conceptual, automated, **serverless** data pipeline that transforms raw operational data into analytics-ready datasets.

---

## Data Challenges (Current System)
- **Inconsistent measurement units:** some meters report energy in Watts (W), others in Kilowatts (kW)
- **Missing readings (NULL values):** Wi‑Fi outages create gaps in time series
- **Inefficient data format:** CSV deliveries not optimized for large-scale historical analytics

---

## Design Goal (Focus on data science logic, not cloud config)
Design—not implement—a conceptual serverless **ETL pipeline** that:
1) Cleans and standardizes energy data  
2) Stores structured data for querying and validation  
3) Archives analytics-optimized data for long-term analysis  
4) Handles failures and retries automatically

**Deliverables:**
- **Task A:** ETL Architecture Diagram (System Design)  
- **Task B:** Transformation Logic & Business Rules  
- **Task C:** Single Record Lifecycle Explanation

**Submission:**
- `ETL_Architecture.md` (+ optional `.drawio/.png/.pdf`)  
- `TransformationRules.md`  
- `RecordLifecycle.md`  
- `Reflection.md`
