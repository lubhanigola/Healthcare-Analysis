# 🏥 Healthcare Analysis Dashboard – From SQL to Power BI Insights  

## 💭 Why I Chose This Dataset
Healthcare is one of the **most dynamic and essential sectors** worldwide. It constantly requires data-driven insights to monitor patient trends, operational efficiency, and financial performance.  
I wanted to explore how **SQL, Data Modeling, and Power BI** together can transform raw healthcare data into meaningful analytics — enabling hospitals and administrators to make **faster, smarter, and more accurate decisions**.

---

## ⚔️ Struggles I Faced

### 🧩 SQL Challenges
While preparing the data model:
- The dataset had **no primary or foreign keys**, so I analyzed each table to identify unique columns and created **relationships manually**.  
- Many columns contained **incorrect data types** (stored as text). These were standardized to **INT, DECIMAL, and DATE** formats.  
- **Date columns** (Admitted, Discharge, and Follow-up Visit Dates) contained several nulls, which I retained as **NULL** instead of imputing — since they represent real hospital scenarios like *ongoing treatments or missed follow-ups*.  
- Ensured that **data integrity** was maintained throughout by enforcing correct relationships.

### 💡 Power BI Challenges
During Power BI development:
- Creating a dynamic **Date Table using DAX** to handle time-based insights was initially complex.  
- Some **slicers didn’t respond dynamically**, requiring relationship tuning and filter management.  
- Designing an interactive **landing page with navigation buttons** between dashboards required UX refinement and visual consistency.  

---

## 💼 Business Problem
Hospitals often face challenges in tracking key KPIs such as **patient satisfaction, average stay duration, and treatment costs**.  
Due to data scattered across different systems, administrators lack a unified view to:
- Monitor **operational efficiency**
- Identify **financial leakages**
- Optimize **resource utilization**
- Improve **patient outcomes**

This project bridges that gap by combining SQL data modeling and Power BI dashboards to deliver a **single source of truth** for hospital operations.

---

## 🎯 Project Objectives
- Clean, transform, and normalize healthcare data using **SQL**.  
- Build a **relational database model** connecting multiple entities (patients, visits, diagnosis, providers, insurance, etc.).  
- Create an **interactive Power BI dashboard** to monitor both *Operational* and *Financial* metrics.  
- Enable hospital management to gain real-time insights into **revenue, admissions, and satisfaction trends**.

---

## ⚙️ Tech Stack

| Tool / Technology | Purpose |
|-------------------|----------|
| 🟨 **MySQL** | Data Cleaning, Transformation & Relationship Modeling |
| 🧩 **Power Query Editor** | Data preprocessing inside Power BI |
| 📊 **Power BI Desktop** | Dashboard Development & Visualization |
| 🔗 **Data Modeling** | Establishing relations across multiple tables |
| 🧠 **DAX (Data Analysis Expressions)** | Used for Calculated Measures, KPIs & Date Intelligence |

---

## 🧾 Dataset
The dataset represents a **multi-department hospital system**, including:
- Patient demographics  
- Visit details (admitted, discharged, follow-up dates)  
- Diagnoses & procedures  
- Treatment, medication, and room charges  
- Provider and insurance information  
- State and city-level data for revenue analysis  

It contains **thousands of records** simulating a real-world hospital’s daily operations and financial transactions.

---

## 💼 Business Problem
Healthcare organizations face challenges in integrating and analyzing large amounts of clinical and operational data.  
Without unified analytics:
- 📉 Resource allocation becomes inefficient  
- 💸 Revenue leakages go unnoticed  
- 🩺 Patient satisfaction cannot be benchmarked  

This project aims to provide **data-backed visibility** into hospital operations, helping decision-makers understand patient flow, cost structure, and key KPIs.

---

## ✨ Key Features

### a) **Healthcare Operations Performance Dashboard**
- **KPI Cards:** Total Patients, Admissions, Discharges, Follow-ups, Satisfaction Score  
- **Donut Chart:** Patient distribution across Admitted, Discharged, and Follow-up statuses  
- **Funnel Chart:** Patient flow by Diagnosis  
- **Bar Chart:** Patients by Age Group  
- **Column Chart:** Referral Source analysis  
- **Map Chart:** Revenue by State  
- **Interactive Buttons:** Navigate between dashboards seamlessly  

### b) **Financial & Operational Insights Dashboard**
- **KPIs:** Total Revenue, Avg Treatment Cost, Avg Length of Stay, Avg Room Daily Rate  
- **Trend Visuals:** Month-over-Month Revenue Comparison  
- **Bar Chart:** Medication Cost by Diagnosis  
- **Funnel Chart:** Patient Cost Breakdown  
- **Map View:** Geographic Revenue Concentration  

---

## 🧮 Power BI DAX Highlights
Several DAX formulas were implemented for calculating performance indicators and date-based intelligence, such as:
- Total Patients  
- Total Admissions / Discharges / Follow-ups  
- Average Treatment Cost per Patient  
- Average Length of Stay  
- Total Revenue (Treatment + Medication + Room Charges)  
- Emergency Visit Percentage  
- Top 3 Diagnoses by Medication Cost  

These DAX expressions helped build **dynamic KPIs** that change instantly with filters and slicers, ensuring real-time interactivity.

---

## 🗂️ Data Modeling
- Created **fact** tables (`visits`) and **dimension** tables (`patients`, `diagnosis`, `providers`, `departments`, `insurance`, `cities`).  
- Added **Date Table** in Power BI for time-based aggregation.  
- Established **many-to-one relationships** across fact and dimension tables.  
- Ensured all relationships used **referential integrity** for accurate insights.  

---

## 🧱 SQL Data Model  
![SQL Data Model](https://github.com/lubhanigola/SQL-Projects/raw/main/Healthcare%20Analysis/SQL%20Data%20Cleaning/SQL%20Data%20Modeling.png)  
🔗 [View SQL Model](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/SQL%20Data%20Cleaning/SQL%20Data%20Modeling.png)

---

## 🔗 Power BI Data Model  
![Power BI Data Model](https://github.com/lubhanigola/SQL-Projects/raw/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Power%20BI%20Data%20Modeling.png)  
🔗 [View Power BI Model](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Power%20BI%20Data%20Modeling.png)

---

## 📊 Dashboard Previews  

### 🩺 Healthcare Operations Performance Overview  
![Healthcare Operations Performance Overview](https://github.com/lubhanigola/SQL-Projects/raw/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Healthcare%20Operations%20Performance%20Overview.png)  
🔗 [View Dashboard](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Healthcare%20Operations%20Performance%20Overview.png)

### 💰 Financial & Operational Insights  
![Financial & Operational Insights](https://github.com/lubhanigola/SQL-Projects/raw/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Financial%20%26%20Operational%20Insights.png)  
🔗 [View Insights Dashboard](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Financial%20%26%20Operational%20Insights.png)

---

## 📂 Power BI File  
📦 [Download Healthcare Project (.pbix)](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Healthcare%20project.pbix)

---

## 📈 Key Insights
- 💵 **Total Revenue:** 3M  
- 👩‍⚕️ **Distinct Patients:** 4,973  
- 🌍 **Top States:** UK & Ireland lead in revenue contribution  
- 🕒 **Average Length of Stay:** 4.88 days  
- 💊 **High-Cost Diagnosis:** Cardiac and Neurology treatments dominate medication expenses  
---

## 🧠 Learnings & Takeaways
- Strengthened knowledge of **SQL data modeling** and **Power BI integration**  
- Understood the importance of **handling NULL values** responsibly  
- Enhanced proficiency in **DAX measures and visual interactivity**  
- Learned how to design dashboards that tell a **cohesive data story**   
---

⭐ *If you found this project insightful, please star the repository and share your feedback!*
