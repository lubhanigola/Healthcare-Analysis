# 🏥 Healthcare Analysis Dashboard – Power BI

A complete healthcare data visualization project that combines **Patient Medical & Demographic** analysis with **Financial & Operational** insights.  

**Explore Full Project File (.pbix):** [US Healthcare Analysis.pbix](https://github.com/lubhanigola/SQL-Projects/raw/main/1/Dashboard%20file%20%26%20snapshot/US%20Healtcare%20Analysis.pbix)  )  

---

## 1) Screenshots (Preview)

 **Data Modelling**  
![Data Model](https://github.com/lubhanigola/SQL-Projects/raw/main/1/Dashboard%20file%20%26%20snapshot/Data%20Modeling.png)  

- **Patient Demographics & Medical Insights Dashboard**  
![Patient Dashboard](https://github.com/lubhanigola/SQL-Projects/raw/main/1/Dashboard%20file%20%26%20snapshot/Patients%20Demographics%20%26%20Medical%20Dashboard.png)  

- **Financial & Operational Insights Dashboard**  
![Financial Dashboard](https://github.com/lubhanigola/SQL-Projects/raw/main/1/Dashboard%20file%20%26%20snapshot/Financial%20%26%20Operational%20Dashboard.png)  

---

## 2) Objectives
✅ Provide a unified view of **patient demographics** and **healthcare finance & operations**  
✅ Monitor KPIs: Total Patients, Avg Age, Avg Billing Amount, Top Medical Condition, Total Billing vs Target, Insurance Provider breakdown  
✅ Support monthly & yearly trend analysis using a dedicated **Date** table  
✅ Enable stakeholders to slice by medical condition, gender, blood type, admission type, hospital, doctor, and insurance provider  

---

## 3) Tech Stack
- **SQL** – Data cleaning & preprocessing  
- **Power Query** – ETL steps inside Power BI  
- **Power BI Desktop** – Dashboard design & visuals  
- **DAX** – Measures for KPIs (Billing, Avg Age, Patients, YTD, MoM%)  
- **Excel / CSV** – Source raw files  

---

## 4) Dataset
Healthcare dataset includes:  
- **Name, Age, Gender, Blood Type**  
- **Medical Condition, Medication, Test Results**  
- **Date of Admission, Discharge Date, Admission Type**  
- **Doctor, Hospital, Insurance Provider**  
- **Room Number**  
- **Billing Amount (numeric column)**  

---

## 5) Business Problem
Healthcare organizations need a consolidated view that links **patient profiles** with **financial performance**. Without a dashboard, it’s difficult to:  
- Identify high-frequency or high-cost medical conditions  
- Monitor billing vs target achievement  
- Understand patient distribution by demographics & admission type  
- Allocate staff, resources, and budgets effectively  

---

## 6) Key Features
- **Patient Demographics & Medical Dashboard:**  
  - KPIs: Top Medical Condition, Total Patients, Avg Age, Blood Types Count  
  - Patients by Age Group (bar chart)  
  - Monthly Patients (trend line)  
  - Admission Type Distribution (donut/treemap)  
  - Patients by Test Results & Insurance Provider  

- **Financial & Operational Dashboard:**  
  - KPIs: Avg Billing Amount, Total Doctors, Hospitals, Insurance Providers  
  - Total Billing vs Target (gauge)  
  - Monthly & Yearly Billing Trends  
  - Billing by Admission Type & Insurance Provider  

---

## 7) Insights Delivered
- **Top Medical Condition:** Hypertension is most frequent  
- **Total Patients:** ~9,807 (baseline for planning)  
- **Avg Age:** 51.14 years  
- **Admission Type Distribution:** Emergency admissions dominate billing (~85.34M)  
- **Average Billing Amount:** 23.37K  
- **Total Billing:** 229.23M vs Target 458.46M (~50% achieved)  
- **Insurance Providers:** Medicare leads (~54M billing), followed by Aetna, Cigna, Blue Cross  
- **Trends:** Monthly & yearly comparisons highlight seasonal and yearly performance  

---

## 8) Use Cases
- **Healthcare Managers** → Monitor patient load & admissions  
- **Finance Teams** → Track billing, insurer performance, target achievement  
- **Clinical Leads** → Focus on high-impact medical conditions  
- **Executives** → Quick view of financial & operational health  
- **Researchers** → Study demographics & condition prevalence  
