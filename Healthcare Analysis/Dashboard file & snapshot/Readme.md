# 📊 Healthcare Data Analysis using Power BI

## 📘 Project Overview
This project extends the healthcare SQL analysis into an **interactive Power BI dashboard**, enabling data-driven insights for hospital operations, patient care, and financial performance.

The Power BI report visualizes key healthcare KPIs such as **patient satisfaction**, **admission trends**, **follow-up rates**, **treatment costs**, and **revenue insights** using multiple charts and DAX-based calculations.  
A custom **date table**, dynamic measures, and advanced DAX functions are used to create accurate and flexible analytics.

---

## 🧠 DAX Measures Used

```DAX
-- 📅 Date Table
DateTable =
ADDCOLUMNS (
    FILTER(
        CALENDAR (MIN(Visits[Date_of_Visit]), MAX(Visits[Date_of_Visit])),
        MONTH([Date]) <> 11 -- Exclude November (11th month)
    ),
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month Name", FORMAT([Date], "MMM"),
    "Quarter", "Q" & FORMAT([Date], "Q"),
    "Year-Month", FORMAT([Date], "YYYY-MM"),
    "Weekday", FORMAT([Date], "DDD"),
    "Weekday Number", WEEKDAY([Date])
)

-- 👥 Total Patients
Total Patients =
DISTINCTCOUNT(patients[Patient_Id])

-- 👶 Age Category
Age Category =
SWITCH(
    patients[Age_Category],
    "Young Adults", "Below 40",
    "Middle Age Adults", "Below 60",
    "Senior Citizen", "Above 60"
)

-- 💰 Avg Treatment Cost per Patient
Avg Treatment Cost per Patient =
DIVIDE(
    SUM(Visits[Treatment_Cost]),
    DISTINCTCOUNT(Visits[Patient_Id])
)

-- 🔁 Avg Follow-Up Rate
Avg Follow Up Rate =
DIVIDE(
    COUNT(visits[Follow_Up_Visit_Date]),
    DISTINCTCOUNT(patients[Patient_Id])
)

-- 🏨 Avg Length of Stay (Days)
Avg Length of Stay (Days) =
AVERAGEX(
    FILTER(
        visits,
        NOT(ISBLANK(visits[Discharge_Date])) &&
        visits[Discharge_Date] >= visits[Date_of_Visit]
    ),
    DATEDIFF(visits[Date_of_Visit], visits[Discharge_Date], DAY)
)

-- 🛏️ Avg Room Daily Rate
Avg Room Daily Rate =
AVERAGE(visits[Room_charges_Daily_Rate])

-- 💊 Medication Cost
Medication Cost =
SUM(visits[Medication_Cost])

-- 🏥 Total Admissions
Total Admissions =
COUNTX(visits, NOT(ISBLANK(visits[Admitted_Date])))

-- 📆 Total MTD
Total Mtd =
TOTALMTD([Total Revenue], DateTable[Date])

-- 💵 Total Room Rate
Total Room Rate =
SUM(visits[Room_charges_Daily_Rate])

-- 🧾 Admitted Patients
Admitted Patients =
CALCULATE(
    COUNTROWS(visits),
    NOT(ISBLANK(visits[Admitted_Date]))
)

-- 🚪 Discharged Patients
Discharged Patients =
CALCULATE(
    COUNTROWS(visits),
    NOT(ISBLANK(visits[Discharge_Date]))
)

-- 🚑 Emergency Visit Percentage
Emergency Visit Perct =
DIVIDE(
    CALCULATE(COUNTROWS(Visits), Visits[Emergency_Visit] = "Yes"),
    COUNTROWS(Visits)
)

-- 🔄 Follow-Up Patients
Follow-Up Patients =
CALCULATE(
    COUNTROWS(visits),
    NOT(ISBLANK(visits[Follow_Up_Visit_Date]))
)

-- 😀 Satisfaction Score
Satisfaction Score =
AVERAGE(visits[Patient_Satisfaction_Score])

-- 💊 Top 3 Medication Cost by Diagnosis
Top 3 Medication Cost by Diagnosis =
CALCULATE(
    SUM(visits[Medication_Cost]),
    FILTER(
        ALL(visits[Diagnosis_Id]),
        RANKX(
            ALL(visits[Diagnosis_Id]),
            SUM(visits[Medication_Cost]),
            ,
            DESC,
            DENSE
        ) <= 3
    )
)

-- 💊 Total Medication Cost
Total Medication Cost =
SUM(visits[Medication_Cost])

-- 💵 Total Revenue
Total Revenue =
SUM(visits[Treatment_Cost]) +
SUM(visits[Medication_Cost]) +
SUM(visits[Room_charges_Daily_Rate])

-- 🧍 Total Visits
Total Visits =
COUNTROWS(visits)

-- 🧾 Treatment Cost
Treatment Cost =
SUM(visits[Treatment_Cost])
