# 🏥 Healthcare Analysis Dashboard – Power BI

A complete healthcare data visualization project that combines **Patient Medical & Demographic** analysis with **Financial & Operational** insights. The dashboard helps healthcare teams monitor patient trends, identify high-impact conditions, and track billing performance — all in one interactive report.

🔗 **Explore Full Project File (.pbix):** [US Healthcare Analysis.pbix](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/US%20Healtcare%20Analysis.pbix)

---

## 📸 Screenshots (Preview)

- **Patient Demographics & Medical Insights Dashboard**  
  ![Patient Dashboard](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Patients%20Demographics%20%26%20Medical%20Dashboard.png)

- **Financial & Operational Insights Dashboard**  
  ![Financial Dashboard](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Financial%20%26%20Operational%20Dashboard.png)

- **Data Model**  
  ![Data Model](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Data%20Modelling.png)

---

## 🎯 Objectives
- Provide a unified view of **patient demographics** and **healthcare finance & operations**.  
- Enable quick monitoring of essential KPIs: Total Patients, Avg Age, Avg Billing Amount, Top Medical Condition, Total Billing (vs Target), Insurance Provider breakdown, Doctors & Hospitals counts.  
- Support month-over-month and year-over-year trend analysis using a dedicated **Date** table.  
- Allow stakeholders to slice by medical condition, gender, blood type, admission type, hospital, doctor, and insurance provider.

---

## 🛠 Tech Stack
- **SQL** — Data cleaning & preprocessing (deduplication, trimming, type conversion, date parsing).  
- **Power Query** — Additional ETL steps inside Power BI (type enforcement, currency strip, date parsing).  
- **Power BI Desktop** — Dashboard design & visuals.  
- **DAX** — Measures for KPIs (Total Billing, Avg Billing, Distinct Patients, Top Condition, YTD Billing, MoM %).  
- **Excel / CSV** — Source raw files (if applicable).

---

## 📂 Dataset
The dataset contains the following columns:

```text
Name
Age
Gender
Blood Type
Medical Condition
Date of Admission
Doctor
Hospital
Insurance Provider
Billing Amount
Room Number
Admission Type
Discharge Date
Medication
Test Results

> **Note:** `Billing Amount` is the only numeric column used for financial calculations. All other columns are categorical or dates.

---

## 💡 Business Problem
Healthcare organizations need a consolidated reporting view that connects **who** the patients are (demographics & conditions) with **how** services are being billed and delivered (billing, admission types, insurance). Without a combined dashboard it is difficult to:

- Identify high-frequency / high-cost medical conditions.  
- Monitor average billing and track total billing vs target.  
- Understand patient distribution by age, gender, admission type and test outcomes.  
- Allocate staff, beds, and budget effectively across hospitals and providers.

---

## 🔑 Key Features

**Main:** Healthcare Analysis Dashboard (contains two sub-dashboards)

### A. Patient Medical & Demographic (Sub-Dashboard)
- KPI cards: **Top Medical Condition**, **Number of Medical Conditions**, **Total Patients**, **Blood Types count**, **Avg Age**.  
- **Patients by Age Group** bar chart (age-buckets).  
- **Monthly Patients** trend line / area chart.  
- **Admission Type** distribution (donut/treemap).  
- **Patients by Test Results** (horizontal bars).  
- **Patients by Insurance Provider** (bar chart).  
- Filters: Medical Condition, Gender, Blood Type, Year, Hospital, Doctor.

### B. Financial & Operational (Sub-Dashboard)
- KPI cards: **Avg Billing Amount**, **Count of Insurance Providers**, **Total Doctors**, **Total Hospitals**.  
- **Total Billing (current) vs Target** gauge.  
- **Monthly Billing Amount** trend (line).  
- **Bill Amount by Admission Type** (treemap).  
- **Yearly Bill Amount** (bar chart).  
- **Billing by Insurance Provider** (bar chart).  
- Filters: Year, Month, Quarter, Age Group, Gender, Admission Type.

---

## 📊 Insights Delivered
- **Top medical condition:** *Hypertension* — flagged as top condition to prioritize preventive programs.  
- **Total patients:** ~**9,807** — quick baseline for capacity planning.  
- **Avg Age:** **51.14** years — useful for service-line planning (geriatrics, chronic care).  
- **Blood types recorded:** 8 distinct groups.  
- **Admission types (counts & billing):** Emergency / Urgent / Elective distribution visible — Emergency billing represents a large share of total bill (~85.34M).  
- **Average billing amount:** **23.37K** (per admission/patient).  
- **Total Billing (current):** **229.23M** vs **Target 458.46M** — indicates ~50% of target achieved.  
- **Insurance provider billing:** Medicare leads billing (~54M), followed by Aetna/Cigna/Blue Cross/United Health Care.  
- **Monthly patient & billing trends:** Seasonality / month-to-month variations visible.  
- **Yearly billing snapshot:** 2020–2023 comparisons show revenue movement over years.

---

## 🚀 Use Cases
- **Healthcare Managers:** Monitor capacity, admissions mix, and costs.  
- **Finance Teams:** Track billing, insurer performance, and target achievement.  
- **Clinical Leads:** Prioritize clinical programs for top conditions (e.g., hypertension).  
- **Executives:** One-page view of operational & financial health.  
- **Researchers:** Analyze demographics, test-result distributions and condition prevalence.

---
