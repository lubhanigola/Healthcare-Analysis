# 🏥 Healthcare Analysis Dashboard   

## 💭 Why I Chose This Dataset
Healthcare is one of the **most dynamic and essential sectors** worldwide. It constantly requires data-driven insights to monitor patient trends, operational efficiency, and financial performance.  

This porject demonstrates how **SQL** can turn raw healthcare data into **actionable insights** for better **decision-making, operational monitoring, and performance analysis**.

---

## ⚔️ Struggles I Faced

### 🧩 SQL Challenges
While preparing the data model:
- The dataset had **no primary or foreign keys**, so I analyzed each table to identify unique columns and created **relationships manually**.  
- Many columns contained **incorrect data types** (stored as text). These were standardized to **INT, DECIMAL, and DATE** formats.  
- **Date columns** (Admitted, Discharge, and Follow-up Visit Dates) contained several nulls, which I retained as **NULL** instead of imputing — since they represent real hospital scenarios like *ongoing treatments or missed follow-ups*.  
- Ensured that **data integrity** was maintained throughout by enforcing correct relationships.

---
## 💼 Business Problem
Healthcare organizations face challenges in integrating and analyzing large amounts of clinical and operational data.  
Without unified analytics:
- 📉 Resource allocation becomes inefficient  
- 💸 Revenue leakages go unnoticed  
- 🩺 Patient satisfaction cannot be benchmarked  

This project aims to provide **data-backed visibility** into hospital operations, helping decision-makers understand patient flow, cost structure, and key KPIs.

---

## 🎯 Project Objectives
- Perform **data cleaning, transformation, and standardization** of raw healthcare datasets using advanced **SQL DDL and DML operations**.  
- Design and implement a **normalized relational database schema** by defining **primary keys, foreign keys, and data integrity constraints** across all entities (patients, visits, cities, departments, diagnosis, insurance, procedures, and providers).  
- Conduct **data validation checks** — including null value handling, data type corrections, duplicate detection, and referential consistency.  
- Derive **data-driven insights** using complex SQL queries such as **aggregations, joins, window functions, and CTEs** to analyze:  
  - Patient demographics and diagnosis patterns  
  - Insurance coverage and payment trends  
  - Department-wise and procedure-wise costs  
  - Length of stay, satisfaction scores, and emergency visit frequency  
- Transform the raw data into a **cleaned analytical dataset** that can be directly used for **decision-making and reporting**.  
---
## ⚙️ Tech Stack

| Tool / Technology | Purpose |
|-------------------|----------|
| 🟨 **MySQL** | Data Cleaning, Transformation, and Complex Query Execution |
| 🧩 **SQL Data Modeling** | Building relationships between entities using Primary & Foreign Keys |
| 🧠 **Advanced SQL Functions** | Using Joins, CTEs, Window Functions, and Aggregations for Insights |
| 🧹 **Data Validation & Quality Checks** | Handling Nulls, Duplicates, and Data Type Corrections |
| 📈 **Analytical SQL Queries** | Generating Actionable Insights on KPIs like Treatment Cost, Stay Duration, and Patient Satisfaction |
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

## ✨ Key Features

### a) **Operational Performance Insights (SQL-Based Analysis)**

- **KPI Metrics:**  
  - 🧍‍♂️ **Total Patients**  
  - 🔁 **Repeat Patients** (patients visiting more than once)  
  - ⏱️ **Average Length of Stay** (calculated from admitted and discharge dates)  
  - 💬 **Average Patient Satisfaction Score**  
  - 🚨 **Emergency vs Normal Visits Count**  

- **Patient Distribution Analysis:**  
  - Patient count by **Diagnosis**, **Department**, **City**, **State**, and **Age Group**  
  - Patients **not discharged yet** (NULL discharge dates)  
  - Patients who **did not take follow-up visits** (NULL follow-up dates)  
  - **Top 3 Diagnoses per Age Group** using SQL window functions  
  - Referral Source performance — which source drives more patients  
  - Room type distribution (Private, Semi-private, General, etc.)  

- **Data Quality Checks:**  
  - Identified and handled **NULL**, **duplicate**, and **inconsistent values** across tables  
  - Verified **referential integrity** using **primary & foreign keys** across 7 entity tables  

---

### b) **Financial & Cost Insights (SQL-Based Metrics)**

- **Financial KPIs:**  
  - 💰 **Total Treatment Cost** and **Medication Cost**  
  - 💵 **Average Treatment Cost by Room Type, Department, and Age Group**  
  - 🏥 **Average Room Charges per Day** (Room Type-wise)  
  - 📅 **Yearly and Monthly Total Cost (Treatment + Medication)**  
  - 🧾 **Insurance Coverage Analysis:**  
    - Total **insured vs non-insured** patients  
    - Revenue insights for **insured patients**  

- **Trend Analysis:**  
  - 📆 **Year-over-Year & Month-over-Month Cost Trends** (AVG & SUM of treatment + medication cost)  
  - 🏆 **Top 3 Diagnoses by Treatment Cost**  
  - 💊 **Top 3 Departments by Medication Cost**  
  - 🌍 **State and City-wise Average Treatment & Medication Cost**  

---

### c) **Data Modeling & Schema Design**
- Built **7 interconnected tables** — `Patients`, `Visits`, `Departments`, `Diagnosis`, `Procedures`, `Providers`, `Insurance`, and `Cities`  
- Defined **Primary & Foreign Keys** for data integrity across all relationships  
- Converted all date fields (`admitted_date`, `discharge_date`, `follow_up_visit_date`, `date_of_visit`) into proper `DATE` format using `STR_TO_DATE()`  
- Created a **cleaned and fully relational schema** — foundation for all analytical SQL queries  

---

### d) **Business Impact**
- Provided a **single source of truth** for hospital operations using SQL alone  
- Enabled hospital management to:  
  - Monitor operational performance  
  - Track patient and financial KPIs  
  - Identify inefficiencies in discharge and follow-up processes  
  - Optimize costs and improve service delivery  
---

## 🧱 SQL Data Model  
![SQL Data Model](https://github.com/lubhanigola/SQL-Projects/raw/main/Healthcare%20Analysis/SQL%20Data%20Cleaning/SQL%20Data%20Modeling.png)  
🔗 [View SQL Model](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/SQL%20Data%20Cleaning/SQL%20Data%20Modeling.png)

---

## 📊 Top 10 Key Insights from SQL Analysis

1. **💵 Total Revenue**  
   - Provides the total revenue generated by the hospital by combining **treatment costs and medication costs** for all patient visits.

2. **👩‍⚕️ Distinct Patients**  
   - Shows the **total number of unique patients** served in the hospital, giving insight into patient volume and reach.

3. **🧠 Top Diagnoses by Patient Count**  
   - Identifies the **most frequent medical conditions** treated, helping hospitals understand **disease prevalence** and resource needs.

4. **🧩 Top 3 Diagnoses per Age Group**  
   - Highlights the **most common diagnoses for each age category**, enabling **age-specific treatment planning** and preventive care strategies.

5. **🏥 Top Departments by Medication Cost**  
   - Reveals departments with the **highest medication expenditure**, which helps in budgeting and **cost optimization**.

6. **⏱️ Average Length of Stay**  
   - Calculates the **average number of days patients stay in the hospital**, providing insights into **operational efficiency** and bed utilization.

7. **🚨 Emergency vs Normal Visits**  
   - Shows the **distribution of emergency versus non-emergency visits**, helping hospitals allocate **resources and staff efficiently**.

8. **🌍 Patients by State & City**  
   - Provides the **geographical distribution of patients**, useful for identifying high-demand areas and planning **outreach or service expansions**.

9. **💵 Average Treatment Cost by Room Type**  
   - Compares the **average treatment costs for different room types**, assisting in **pricing strategies and cost management**.

10. **🔁 Repeat Patients**  
    - Highlights the **number of patients with multiple visits**, offering insights into **patient loyalty, follow-up needs, and chronic care management**.
---

## Use Cases

By consolidating diverse healthcare datasets into interactive dashboards, this project empowers stakeholders to make data-driven decisions that enhance patient care, operational efficiency, and financial management for:
**🏢 Hospital Administrators & Managers**  
   - Monitor **patient flow, admissions, and discharges**, track departmental costs, and optimize **resource allocation** for improved operational efficiency.
     
**👩‍⚕️ Doctors & Clinical Staff**  
   - Identify **top diagnoses**, monitor **treatment outcomes**, and plan **age-specific or condition-specific care**, improving **patient outcomes**.

**📊 Financial & Operations Teams**  
   - Analyze **treatment and medication costs**, monitor **insurance coverage**, and evaluate **revenue streams** to guide **budgeting and cost optimization**.

**🌍 Policy Makers & Public Health Officials**  
   - Understand **regional patient demographics, disease prevalence, and hospital utilization patterns** to inform **healthcare policies and resource planning**.

**🧠 Researchers & Analysts**  
   - Explore **correlations between patient demographics, treatment costs, and service usage**, enabling studies on **healthcare trends and operational efficiency**.
---

## 🧠 Learnings & Takeaways
- Strengthened knowledge of **SQL data cleaning, transformation, and relational modeling**  
- Gained experience in **handling NULL values and data inconsistencies** efficiently  
- Learned how to **derive actionable insights** using complex SQL queries and aggregations  
- Developed skills to **analyze operational and financial KPIs** from raw healthcare data  
- Understood how to structure queries to **support strategic decision-making** in healthcare operations  
---
