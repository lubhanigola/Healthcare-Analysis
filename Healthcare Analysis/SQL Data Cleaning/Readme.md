# 🏥 Healthcare Data Analysis using SQL

## 📘 Project Overview
This project simulates a **real-world healthcare analytics system** built entirely in **MySQL**.  
It focuses on cleaning, structuring, and analyzing hospital-related data to generate valuable insights for better decision-making.

The dataset represents hospital operations, including **patients, providers, departments, diagnosis, insurance, visits, procedures, and city information**.  
Since the raw data did not include relationships or constraints, the project involved creating a **complete relational schema** with **primary keys, foreign keys, and data cleaning processes**.

After data modeling, **31 analytical SQL queries** were developed to uncover insights related to:
- Patient demographics and trends  
- Treatment costs by department and diagnosis  
- Repeat patients and emergency cases  
- Yearly and monthly visit trends  
- Average hospital stay duration  
- Department and insurance performance metrics  

This project demonstrates end-to-end **data analysis, modeling, and reporting** capabilities using SQL — reflecting tasks commonly performed by **Data Analysts and BI professionals** in the healthcare domain.

---

## 🎯 Project Objectives

1. **Data Cleaning & Preparation**
   - Standardize inconsistent column names for clarity.  
   - Convert date fields using `STR_TO_DATE()` for proper formatting.  
   - Replace blank fields with `NULL` values.  
   - Ensure all data types are correctly defined (e.g., `INT`, `DATE`, `VARCHAR`).  
   - Add derived columns (e.g., `Age_Category`) for segmentation.

2. **Database Design & Relationships**
   - Design a **Star Schema** where:
     - `visits` → Fact table  
     - `patients`, `providers`, `departments`, `diagnosis`, `insurance`, `procedures`, and `cities` → Dimension tables  
   - Define **Primary Keys** for dimension tables.  
   - Link tables with **Foreign Keys** in the fact table for referential integrity.  

3. **Data Validation & Quality Checks**
   - Detect and remove duplicate records.  
   - Identify and replace blank or null entries.  
   - Check data completeness and logical consistency (e.g., valid age, admission/discharge dates).  

4. **Analytical SQL Querying**
   - Derive KPIs such as patient count, total cost, average stay duration, and treatment trends.  
   - Perform segmentation by age category, diagnosis, insurance provider, and department.  
   - Identify repeat patients, pending discharges, and emergency cases.  
   - Generate yearly and monthly performance summaries.

---

## 🛠️ SQL Script for Data Cleaning & Analysis

```sql
/* Creation of Separate Database */ 
Create Database Project1;
use project1;
show tables;
/*Sanity check of all tables and respective columns*/
select * from cities;
desc cities;
Alter table cities
modify column city varchar(50),
modify column state varchar(50);

Select * from departments;
desc departments;
Alter table departments
modify column department varchar(20);

Select * from diagnoses;
desc diagnoses;
Alter table diagnoses 
rename to diagnosis;
Alter table diagnosis
modify column Diagnosis varchar(50);

select * from insurance;
desc insurance;
Alter table insurance
change column `insurance provider` insurance_provider varchar(50);
Alter table insurance
rename column `insurance id` to insurance_id;

select * from patients;
desc patients;
Alter table patients
rename column `patient id` to patient_id,
change column `patient name` patient_name varchar(50),
modify column Gender varchar(20),
rename column `city id` to city_id,
modify column race varchar(50);

select * from procedures;
desc procedures;
alter table procedures
rename column `procedure id` to procedure_id,
modify column `Procedure` varchar(20);

select * from providers;
desc providers;
alter table providers
rename column `provider id` to provider_id,
change column `provider name` provider_name varchar(50),
modify column gender varchar(10),
modify column nationality varchar(20);

select * from visits;
desc visits;
Alter table visits
rename column `date of visit` to Date_of_visit;

UPDATE visits
SET Date_of_visit = STR_TO_DATE(Date_of_visit, '%m/%d/%Y');

Alter table visits
modify column Date_of_Visit date,
rename column `patient id` to patient_id,
rename column `provider id` to provider_id,
rename column `department id` to department_id,
rename column `diagnosis id` to diagnosis_id,
rename column `procedure id` to procedure_id,
rename column `insurance id` to insurance_id,
change column `service type` service_type varchar(50),
rename column `treatment cost` to treatment_cost,
rename column `medication cost` to medication_cost,
rename column `patient satisfaction score` to patient_satisfaction_score,
change column `referral source` referral_source varchar(50),
change column `emergency visit` emergency_visit varchar(10),
change column `payment status` payment_status varchar(20),
change column `room type` room_type varchar(50),
change column `room charges(daily rate)` room_charges_daily_rate int;

Alter table visits
rename column `follow-up visit date` to follow_up_visit_date;
select follow_up_visit_date from visits;

/* Challenge 1 to change dates columns in visits*/

create table new_visits as
select * from visits;

SELECT follow_up_visit_date
FROM new_visits
WHERE follow_up_visit_date is null;
Update new_visits
set follow_up_visit_date = str_to_date(follow_up_visit_date,'%m/%d/%Y')
where follow_up_visit_date != '';
/* replacing blank with null values */
Update new_visits
set follow_up_visit_date = Null
where follow_up_visit_date = '';

Alter table new_visits
modify column follow_up_visit_date date;

/*Dishcarge Date & Admitted Date Columns*/

Alter table new_visits
rename column `discharge date` to Discharge_Date;

select Discharge_Date from new_visits;

Update new_visits
set Discharge_Date = str_to_date(Discharge_Date, '%m/%d/%Y')
where Discharge_Date != '';
/* replacing blank with null values */
UPDATE new_visits
SET Discharge_Date = NULL
WHERE Discharge_Date = '';

Alter table new_visits
modify column Discharge_Date date;

Alter table new_visits
rename column `admitted date` to Admitted_Date;

Select Admitted_Date from new_visits
where Admitted_Date != '';

Update new_visits
set admitted_Date = str_to_date(admitted_date,'%m/%d/%Y')
where admitted_date != '';
/* replacing blank with null values */
Update new_visits
set admitted_Date = Null
where admitted_date = '';

Alter table new_visits
modify column admitted_date date;

/* Challenge 2 changing table name*/
drop table visits;

rename table new_visits to visits;
select * from visits;
desc visits;
dselect insurance_coverage from visits;
ALTER TABLE visits
rename column `insurance coverage` to insurance_coverage;
/* replacing blank with null values */
ALTER TABLE visits MODIFY COLUMN insurance_coverage DECIMAL(10,2);

Alter table visits
rename column Date_of_Visit to date_of_visit,
rename column Discharge_Date to discharge_date;

Alter table cities
rename column `City ID` to City_Id,
add primary key(City_Id);

Alter table cities
rename column `city` to City,
rename column `state` to State;
/*Creating Relations between tables */

Alter table departments
rename column `Department ID` to Department_Id,
rename column `department` to Department,
add primary key(Department_Id);

Alter table diagnosis
rename column `Diagnosis ID` to Diagnosis_Id,
add primary key(Diagnosis_Id);

Alter table insurance
rename column insurance_id to Insurance_Id,
rename column insurance_provider to Insurance_Provider,
add primary key(Insurance_Id);

Alter table patients
rename column patient_id to Patient_Id,
rename column patient_name to Patient_name,
rename column city_id to City_ID,
rename column race to Race,
add primary key(Patient_Id),
ADD CONSTRAINT fk_city
FOREIGN KEY (City_Id) REFERENCES cities(City_id);

Alter table procedures
rename column procedure_id to Procedure_Id,
add primary key (Procedure_Id);

Alter table providers
rename column provider_id to Provider_Id,
rename column provider_name to Provider_name,
rename column gender to Gender,
rename column nationality to Nationality,
add primary key(Provider_Id);

Alter table visits
rename column patient_id to Patient_Id,
add constraint fk_patients
FOREIGN KEY (Patient_Id) REFERENCES patients(Patient_Id),
rename column provider_id to Provider_Id,
add constraint fk_provider
FOREIGN KEY (Provider_Id) REFERENCES providers(Provider_Id),
rename column department_id to Department_Id,
add constraint fk_departments
FOREIGN KEY (Department_Id) REFERENCES departments(Department_Id),
rename column diagnosis_id to Diagnosis_Id,
add constraint fk_diagnosis
FOREIGN KEY (Diagnosis_Id) REFERENCES diagnosis(Diagnosis_Id),
rename column procedure_id to Procedure_Id,
add constraint fk_procedure
FOREIGN KEY (Procedure_Id) REFERENCES procedures(Procedure_Id),
rename column insurance_id to Insurance_Id,
add constraint fk_insurance
FOREIGN KEY (Insurance_Id) REFERENCES insurance(Insurance_Id),
rename column date_of_visit to Date_of_Visit,
rename column service_type to Service_Type,
rename column treatment_cost to Treatment_Cost,
rename column medication_cost to Medication_Cost,
rename column follow_up_visit_date to Follow_Up_Visit_Date,
rename column patient_satisfaction_score to Patient_Satisfaction_Score,
rename column referral_source to Referral_Source,
rename column emergency_visit to Emergency_Visit,
rename column payment_status to Payment_Status,
rename column discharge_date to Discharge_Date,
rename column admitted_date to Admitted_Date,
rename column room_type to Room_Type,
rename column insurance_coverage to Insurance_Coverage,
rename column room_charges_daily_rate to room_charges_daily_rate;

Alter table visits
rename column room_charges_daily_rate to 
Room_charges_Daily_Rate;

Select * from cities;
Select * from departments;
Select * from diagnosis;
Select * from insurance;
select * from patients
Select * from procedures;
Select * from providers;
Alter table providers
modify column image blob;
/*Checking Duplicacy in dimenstion tables*/
SELECT Patient_id, COUNT(*) as counts
FROM patients
GROUP BY Patient_id
HAVING COUNT(*) > 1;

select city_id, count(*) as counts from cities 
group by city_id
having count(*) > 1;

select department_id, count(*) as counts from departments
group by department_id
having count(*) > 1;

select diagnosis_id, count(*) as counts 
from diagnosis
group by diagnosis_id
having count(*) > 1;

select insurance_id, count(*) as counts 
from insurance
group by insurance_id
having count(*) > 1;

select procedure_id, count(*) as counts 
from procedures
group by procedure_id
having count(*) > 1;

select provider_id, count(*) as counts 
from providers
group by provider_id
having count(*) > 1;

/*Checking missing values*/
select count(*) from visits
where follow_up_visit_date is null;

select count(*) from visits
where discharge_date is null;

select count(*) from visits
where admitted_date is null;

select count(*) from visits
where Insurance_coverage is null;

select count(*) from visits
where Room_charges_Daily_rate is null;

/* Insight 1 Patients by Insurance Provider*/
select i.Insurance_provider,
count(distinct v.patient_id) as Total_Patients
from insurance i join visits v on
i.insurance_id = v.insurance_id
group by i.Insurance_provider;

/*Insight 2 Patients by Diagnosis*/
select d.Diagnosis,
count(distinct v.patient_id) as Total_Patients
from Diagnosis d 
join visits v 
on d.diagnosis_id = v.diagnosis_id
group by d.Diagnosis;

/*Insight 3 Patients by age*/
Alter table Patients
add column Age_Category varchar (50);

Update Patients
set Age_Category = case when
age >= 18 and age <=40 then 'Young Adults'
when age >=41 and age <=60 then 'Middle Age Adults'
else 'Senior Citizen'
End;

Select 
p.Age_Category,
count(distinct v.patient_id) as Total_patients
from patients p
join visits v
on p.patient_id = v.patient_id
group by p.age_category;

/* Insight 4 Patients by state and city*/
select  c.state,
c.city,
count(distinct v.patient_id) as Total_Patients
from visits v
join patients p on 
v.patient_id = p.patient_id
join cities c
on p.city_id = c.city_id
group by c.state,
c.city;
/* Insight 5 Patients by each city who has not discharged yet*/
select c.city,
count(distinct v.patient_id) as Total_Patients
from cities c
join patients p
on c.city_id = p.city_id
join visits v
on v.patient_id = p.patient_id
where v.discharge_date is null
group by c.city
order by Total_Patients desc;

/* Insight 6 Patients by each city who did not take follow up*/
select c.city,
count(distinct v.patient_id) as Total_Patients
from cities c
join patients p
on c.city_id = p.city_id
join visits v
on v.patient_id = p.patient_id
where v.follow_up_visit_date is null
group by c.city
order by Total_Patients desc;

/*Insight 7 Total patients by age group, city, diagnosis */
select p.age_category,
c.city,
d.diagnosis,
count(distinct v.patient_id) as Total_Patients
from cities c
join patients p
on c.city_id = p.city_id
join visits v
on p.patient_id = v.patient_id
join diagnosis d
on d.diagnosis_id = v.diagnosis_id
group by p.age_category,
c.city, d.diagnosis;

/*Insight 8 Patients count of each patient satisfaction score &
patient counts by referral_source*/

select Patient_Satisfaction_Score,
count(*) as Total_Score
from visits
group by Patient_Satisfaction_Score
order by Patient_Satisfaction_Score;

select Referral_Source,
count(*) as Total_Score
from visits
group by Referral_Source
order by Total_Score;

/* Insight 9 Count of insuranced covered patients 
and non insurance covered
patients */

Update visits set insurance_coverage = 0.0 
where insurance_coverage = '';

select 
count(*) as insured_counts
from visits
where insurance_Coverage != 0.0;

select 
count(*) as non_insured_counts
from visits
where insurance_Coverage = 0.0;

/*Insight 10 
Count how many patients used each service type */
select service_type,
count(*) as total_counts
from visits
group by service_type;

/* Insight 11 
Count how many patients used each service type:
*/
select service_type,
count(distinct patient_id) as total_counts
from visits
group by service_type;

/* Insight 12
Totals Visits for each procedure*/

select p.procedure,
count(*) as Total_Counts
from visits v
join procedures p
on p.procedure_id = v.procedure_id
group by p.procedure
order by Total_Counts desc;

/* Insight 13
Patients count who paid the bill and still pending*/
select 
sum(case when payment_status = 'Paid' then 1 else 0 end)
as Paid_bill,
sum(case when payment_status = 'Pending' then 1 else 0 end)
as Pending_bill
from visits;

/* Insight 14 
Patients count by room type */
update visits
set room_type = 'No room alloted'
where room_type = 'N/A';

SELECT room_type, 
COUNT(DISTINCT patient_id) AS total_patients
FROM visits
GROUP BY room_type;

/* Insight 15*
Yearly & monthly patient counts*/
select
year(date_of_visit) as Year_num,
month(date_of_visit) as month_num,
count(distinct patient_id) as total_patients
from visits
group by Year_num, month_num;

/* Insight 16
Total patients in last year */
SELECT COUNT(DISTINCT patient_id) AS total_patients_last_year
FROM visits
WHERE date_of_visit >= (CURDATE() - INTERVAL 1 YEAR);

/* Insight 17
Repeat Patients */
SELECT patient_id, COUNT(*) AS visit_count
FROM visits
GROUP BY patient_id
HAVING COUNT(*) > 1;

/*Insight 18
Average Length of Stay */
SELECT AVG(DATEDIFF(discharge_date, admitted_date)) AS avg_stay
FROM visits
WHERE discharge_date IS NOT NULL;

/*Insight 19
Top 3 Diagnosis by each Age Group*/
with age_groups_diagnosis as (select p.age_category,
d.diagnosis,
count(d.diagnosis) as Total_diagnosis
from patients p
join visits v 
on p.patient_id = v.patient_id
join diagnosis d
on v.diagnosis_id = d.diagnosis_id
group by p.age_category, d.diagnosis),
ranking as (
select age_category, diagnosis,
Total_diagnosis,
row_number () over (partition by age_category
order by total_diagnosis desc) as rn
from age_groups_diagnosis)
select age_category, diagnosis,
Total_diagnosis
from ranking where rn <= 3;

/* Insight 20 
Top 3 Diagnosis by treatment_cost */
select d.diagnosis,
sum(v.treatment_cost) as total_treatment_cost
from visits v
join diagnosis d
on d.diagnosis_id = v.diagnosis_id
group by d.diagnosis
order by total_treatment_cost desc
limit 3;

/* Insight 21
Top 3 departments by medication_cost */
select d.department,
sum(v.medication_cost) as total_medication_cost
from visits v
join departments d
on d.department_id = v.department_id
group by d.department
order by total_medication_cost desc
limit 3;

/* Insight 22
Avg Treatment cost by room type*/
select room_type,
round(avg(treatment_cost),2) as Total_cost
from visits
group by room_type;

/* Insight 23 
Emergency Visit count */
select 
sum(case when
emergency_visit = 'Yes' then 1 else 0 end) as Emergency_Visits,
sum(case when
emergency_visit = 'No' then 1 else 0 end) as Normal_Visits
from visits;

/* Insight 24 
Avg Room Charges*/
select 
room_type,
round(avg(room_charges_daily_rate),2) as avg_room_charges
from visits
group by room_type;

/* Insight 25
city and state wise avg medication_cost */
/* City wise */
SELECT 
  c.state,
  ROUND(AVG(v.medication_cost), 2) AS avg_medication_cost
FROM visits v
JOIN patients p ON v.patient_id = p.patient_id
JOIN cities c ON p.city_id = c.city_id
GROUP BY c.state
ORDER BY avg_medication_cost DESC;

/* State wise */ 
SELECT 
  c.city,
  ROUND(AVG(v.medication_cost), 2) AS avg_medication_cost
FROM visits v
JOIN patients p ON v.patient_id = p.patient_id
JOIN cities c ON p.city_id = c.city_id
GROUP BY c.city
ORDER BY avg_medication_cost DESC;

/* Insight 26
Treatment cost by age group */
SELECT 
  p.age_category,
  ROUND(AVG(v.treatment_cost), 2) AS avg_treatment_cost
FROM visits v
JOIN patients p ON v.patient_id = p.patient_id
GROUP BY p.age_category
ORDER BY avg_treatment_cost DESC;

/* Insight 27
Avg Treatment Cost by Department*/
SELECT 
  d.department,
  ROUND(AVG(v.treatment_cost), 2) AS avg_treatment_cost
FROM visits v
JOIN departments d ON v.department_id = d.department_id
GROUP BY d.department
ORDER BY avg_treatment_cost DESC;

/* Insight 28
Avg medication and treatment cost by year */ 
select 
year(date_of_visit) as year_num,
round(avg(medication_cost),2) as avg_med_cost,
round(avg(treatment_cost),2) as avg_treatment_cost
from visits 
group by year_num;

/*Insight 29
Monthly Avg Treatment and Medication Cost*/
SELECT 
  YEAR(date_of_visit) AS year,
  MONTH(date_of_visit) AS month,
  ROUND(AVG(treatment_cost), 2) AS avg_treatment_cost,
  ROUND(AVG(medication_cost), 2) AS avg_medication_cost
FROM visits
GROUP BY YEAR(date_of_visit), MONTH(date_of_visit)
ORDER BY year, month;

/* Insight
30
Total Cost per Visit (Treatment + Medication) by Department*/

SELECT 
  d.department,
  ROUND(AVG(v.treatment_cost + v.medication_cost), 2) AS avg_total_visit_cost
FROM visits v
JOIN departments d ON v.department_id = d.department_id
GROUP BY d.department
ORDER BY avg_total_visit_cost DESC;

/*Insight 31
Yearly Total Cost (Treatment + Medication)*/
SELECT 
  YEAR(date_of_visit) AS year,
  ROUND(SUM(treatment_cost + medication_cost), 2) AS total_cost
FROM visits
GROUP BY YEAR(date_of_visit)
ORDER BY year;

/*Monthly Total Cost (Treatment + Medication)*/
SELECT 
  YEAR(date_of_visit) AS year,
  MONTH(date_of_visit) AS month,
  ROUND(SUM(treatment_cost + medication_cost), 2) AS total_cost
FROM visits
GROUP BY YEAR(date_of_visit), MONTH(date_of_visit)
ORDER BY year, month;
