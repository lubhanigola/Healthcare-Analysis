# 🏥 Healthcare Analysis Dashboard – From SQL to Power BI Insights  

## 💭 Why I Chose This Dataset
Healthcare is one of the **most dynamic and essential sectors** worldwide. It constantly requires data-driven insights to monitor patient trends, operational efficiency, and financial performance.  
I wanted to explore how **data modeling, SQL, and Power BI** together can transform raw healthcare data into meaningful analytics — enabling hospitals and administrators to make **faster, smarter, and more accurate decisions**.

---

## ⚔️ Struggles I Faced

### 🧩 SQL Challenges
While preparing the data model:
- I found **no primary or foreign keys** in the raw dataset. To resolve this, I analyzed each table to identify columns with **unique values** and created **relationships** manually.  
- Many columns had incorrect or **text-based data types**. I converted them into the proper types (e.g., INT, DATE, DECIMAL).  
- **Date columns** such as *Admitted Date*, *Discharge Date*, and *Follow-up Visit Date* contained several null values.  
  - These couldn’t be replaced with dummy values since they represented **real-world hospital states** (patients still admitted, missed follow-ups, or pending discharges).  
  - Hence, I preserved them as **NULL** for data integrity and future updates.

### 💡 Power BI Challenges
In Power BI:
- Creating a **Date Table** for time intelligence was tricky — I had to ensure it dynamically covered all `Visit` dates.  
- Some **slicers didn’t update visuals dynamically**, so I had to carefully choose the ones connected correctly to the relationships.  
- Designing an interactive landing page that lets users **navigate between dashboards using buttons** required layout experimentation and attention to UX consistency.

---

## 💼 Business Problem
Hospitals often struggle to track **key metrics** like patient satisfaction, referral patterns, and treatment efficiency due to scattered data across multiple systems.  
Without integration:
- Decision-making becomes **slow and fragmented**  
- Financial inefficiencies remain **unnoticed**  
- Operational performance cannot be **benchmarked**  

This project solves that by integrating SQL data modeling with Power BI to provide a **unified analytical view** of hospital operations and financial outcomes.

---

## 🎯 Project Objective
- Build a **normalized SQL database** for healthcare operations.  
- Clean, transform, and relate data across multiple entities such as patients, visits, providers, and diagnoses.  
- Develop a **Power BI dashboard** with interactive KPIs, filters, and dynamic visuals.  
- Help hospital administrators monitor **patient trends, satisfaction scores, and revenue** in real time.  

---

## ⚙️ Project Workflow

### **Step 1: SQL Data Preparation**
- Created tables: **patients, visits, providers, departments, procedures, diagnosis, insurance, cities**.  
- Assigned **primary and foreign keys** to establish relational integrity.  
- Cleaned columns and **standardized data types** (e.g., INT, VARCHAR, DATE).  
- Verified nulls and ensured **logical consistency** for dates and costs.  
- Exported the final structured data to integrate with Power BI.

### **Step 2: Power BI Development**
- Imported all SQL tables and created a **Date Table** using DAX.  
- Established relationships across all dimension and fact tables.  
- Built two pages in Power BI:
  - **Healthcare Operations Performance Overview**
  - **Financial & Operational Insights**
- Added **buttons for navigation** between dashboards.  
- Designed visuals including:
  - KPI Cards (Patient Count, Revenue, Avg Stay, Satisfaction)
  - Map Visualization (Revenue by State)
  - Donut, Funnel, and Bar Charts (Diagnosis, Age Group, Referral Source)
  - Line Charts (Revenue Trends)

---

## 🧱 SQL Data Model  
**Preview:**  
![SQL Data Model](https://github.com/lubhanigola/SQL-Projects/raw/main/Healthcare%20Analysis/SQL%20Data%20Cleaning/SQL%20Data%20Modeling.png)  
**Accessible Link:** [View SQL Model](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/SQL%20Data%20Cleaning/SQL%20Data%20Modeling.png)

---

## 🔗 Power BI Data Model  
**Preview:**  
![Power BI Data Model](https://github.com/lubhanigola/SQL-Projects/raw/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Power%20BI%20Data%20Modeling.png)  
**Accessible Link:** [View Power BI Model](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Power%20BI%20Data%20Modeling.png)

---

## 📋 Dashboard Overview Page  
**Preview:**  
![Dashboard Overview](https://github.com/lubhanigola/SQL-Projects/raw/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Dashboard%20Overview.png)  
**Accessible Link:** [View Overview Page](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Dashboard%20Overview.png)

---

## 🩺 Healthcare Operations Performance Overview  
**Preview:**  
![Healthcare Operations Performance Overview](https://github.com/lubhanigola/SQL-Projects/raw/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Healthcare%20Operations%20Performance%20Overview.png)  
**Accessible Link:** [View Operations Dashboard](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Healthcare%20Operations%20Performance%20Overview.png)

---

## 💰 Financial & Operational Insights  
**Preview:**  
![Financial & Operational Insights](https://github.com/lubhanigola/SQL-Projects/raw/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Financial%20%26%20Operational%20Insights.png)  
**Accessible Link:** [View Financial Insights](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Financial%20%26%20Operational%20Insights.png)

---

## 📂 Download Power BI File  
You can download and explore the **interactive Power BI dashboard (.pbix file)** used in this project.  
> **File Link:** [Healthcare Project – Power BI File (.pbix)](https://github.com/lubhanigola/SQL-Projects/blob/main/Healthcare%20Analysis/Dashboard%20file%20%26%20snapshot/Healthcare%20project.pbix)

*(Open the link → Click the “Download raw file” option in GitHub to save the PBIX file locally.)*

---

## 📊 Key Insights
- 💵 **Total Revenue:** 3M  
- 👩‍⚕️ **Distinct Patients:** 4973  
- 🌍 **UK and Ireland** generated maximum state-wise revenue.  
- 🕒 **Average Length of Stay:** 4.88 days  
---

## 🧠 Learnings & Takeaways
- Developed strong understanding of **data modeling in SQL** and **Power BI integration**.  
- Improved DAX logic application for **date intelligence and KPIs**.  
- Learned to maintain data integrity by **handling NULL values thoughtfully**.  
- Enhanced storytelling and dashboard design using **interactive visuals and navigation**.  

---

## 🧰 Tech Stack
| Tool / Language | Purpose |
|------------------|----------|
| **MySQL** | Data modeling, cleaning, and querying |
| **Power BI** | Visualization and analytics |
| **DAX** | Calculated columns, measures, and date intelligence |

---

## 🚀 Future Improvements
- Automate SQL data refresh using **Python or Power Automate**  
- Build **live dashboards** linked directly to the SQL server  
- Create a **predictive model** for patient readmission analysis using Python  
- Integrate healthcare data with **external public datasets** (e.g., CDC or WHO metrics)

---

## 👩‍💻 Author
**Name:** Lubhani  
**Role:** Data Analyst (Healthcare Analytics Project)  
**Created:** October 2025  
**Tools:** MySQL | Power BI | DAX | Data Modeling  

---

⭐ *If you found this project insightful, don’t forget to star the repository!*
