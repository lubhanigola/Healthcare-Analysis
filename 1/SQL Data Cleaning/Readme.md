# 🏥 US Healthcare Data Cleaning Script – SQL

This project demonstrates the step-by-step data cleaning and preprocessing performed on the **US Healthcare dataset** using SQL. 
The goal is to standardize columns, clean missing/incorrect values, and prepare the ## 🛠️ SQL Script for Data Cleaning

```sql
-- *******************************************************
-- Healthcare Data Cleaning SQL Script
-- *******************************************************

-- 1) Create Database
CREATE DATABASE Maven_healthcare;
USE Maven_healthcare;

-- 2) Renaming & Standardizing Columns
ALTER TABLE us_healthcare
CHANGE COLUMN `ï»¿Name` Patient_Name VARCHAR(50);

ALTER TABLE us_healthcare
RENAME COLUMN blood_type TO Blood_Type;

ALTER TABLE us_healthcare
CHANGE COLUMN `Medical Condition` Medical_condition VARCHAR(50),
CHANGE COLUMN `Doctor` Doctor VARCHAR(100),
CHANGE COLUMN `Hospital` Hospital VARCHAR(200),
CHANGE COLUMN `Insurance Provider` Insurance_Provider VARCHAR(100),
RENAME COLUMN `Billing Amount` TO Billing_Amount,
RENAME COLUMN `Room Number` TO Room_No,
CHANGE COLUMN `Admission Type` Admission_Type VARCHAR(50),
CHANGE COLUMN `Medication` Medication VARCHAR(20),
CHANGE COLUMN `test results` Test_Results VARCHAR(20);

-- 3) Cleaning Gender Column
UPDATE us_healthcare
SET gender = 'Male'
WHERE gender = 'M';

ALTER TABLE us_healthcare
CHANGE COLUMN `gender` Gender VARCHAR(20);

UPDATE us_healthcare
SET Gender = TRIM(Gender);

-- 4) Patient Name & Blood Type Cleaning
UPDATE us_healthcare
SET patient_name = TRIM(patient_name);

UPDATE us_healthcare
SET blood_type = TRIM(blood_type);

UPDATE us_healthcare
SET Blood_type = 'AB-ve' WHERE blood_type = 'AB negative';
UPDATE us_healthcare
SET Blood_type = 'AB-' WHERE blood_type = 'AB-ve';
UPDATE us_healthcare
SET blood_type = 'B+' WHERE blood_type = 'B+ve';
UPDATE us_healthcare
SET blood_type = 'O+' WHERE blood_type = 'O+ve';
UPDATE us_healthcare
SET blood_type = 'A+' WHERE blood_type = 'A+ve';
UPDATE us_healthcare
SET blood_type = 'O+' WHERE blood_type = '0+';
UPDATE us_healthcare
SET blood_type = 'O-' WHERE blood_type = 'O neg';

-- 5) Cleaning Age & Medical Condition
UPDATE us_healthcare
SET age = TRIM(Age);

UPDATE us_healthcare
SET medical_condition = TRIM(medical_condition);

UPDATE us_healthcare
SET Medical_condition = 'Arthritis' WHERE medical_condition = 'ARTHRITIS';
UPDATE us_healthcare
SET Medical_condition = 'Hypertension' WHERE medical_condition = 'hypertension';

-- 6) Insurance Provider & Room Number
UPDATE us_healthcare
SET insurance_provider = 'United Health Care' WHERE insurance_provider = 'UnitedHealthcare';

UPDATE us_healthcare
SET Insurance_Provider = TRIM(Insurance_Provider);
UPDATE us_healthcare
SET room_no = TRIM(room_no);

-- 7) Date Cleaning – Admission & Discharge
ALTER TABLE us_healthcare
RENAME COLUMN `Date of Admission` TO Date_of_Admission,
RENAME COLUMN `Discharge Date` TO Discharge_Date;

ALTER TABLE us_healthcare
ADD COLUMN new_admissiong_date DATE;

UPDATE us_healthcare
SET new_admissiong_date = CASE
    WHEN date_of_admission LIKE '%-%-%' THEN STR_TO_DATE(date_of_admission, '%d-%m-%Y')
    WHEN date_of_admission LIKE '%,%' THEN STR_TO_DATE(date_of_admission, '%W, %e %M %Y')
END;

ALTER TABLE us_healthcare DROP COLUMN date_of_admission;
ALTER TABLE us_healthcare
RENAME COLUMN new_admissiong_date TO Date_of_admission;
UPDATE us_healthcare SET Date_of_Admission = TRIM(date_of_admission);
ALTER TABLE us_healthcare MODIFY COLUMN Date_of_Admission DATE AFTER Medical_condition;

ALTER TABLE us_healthcare ADD COLUMN new_discharge_date DATE AFTER discharge_date;

UPDATE us_healthcare
SET new_discharge_date = CASE
    WHEN discharge_date LIKE '%-%-%' THEN STR_TO_DATE(discharge_date, '%d-%m-%Y')
    WHEN discharge_date LIKE '%,%' THEN STR_TO_DATE(discharge_date, '%W, %e %M %Y')
END;

ALTER TABLE us_healthcare DROP COLUMN discharge_date;
ALTER TABLE us_healthcare
RENAME COLUMN new_discharge_date TO Discharge_Date;
UPDATE us_healthcare SET Discharge_Date = TRIM(discharge_date);

-- 8) Other Column Cleaning
UPDATE us_healthcare
SET admission_type = 'Emergency' WHERE admission_type = 'Emer';

UPDATE us_healthcare SET admission_type = TRIM(admission_type);
UPDATE us_healthcare SET medication = TRIM(medication);
UPDATE us_healthcare SET test_results = TRIM(test_results);
UPDATE us_healthcare SET Doctor = TRIM(Doctor);
UPDATE us_healthcare SET Hospital = TRIM(Hospital);
UPDATE us_healthcare SET Billing_Amount = TRIM(Billing_Amount);

-- 9) Add Primary Key
ALTER TABLE us_healthcare
ADD COLUMN Patient_ID INT AUTO_INCREMENT PRIMARY KEY;

ALTER TABLE us_healthcare
MODIFY COLUMN Patient_ID INT AUTO_INCREMENT FIRST;



