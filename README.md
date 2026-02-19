📊 HR Attrition Analysis & Risk Modeling Dashboard (Power BI)
🎯 Project Objective

This project was designed to simulate a real-world HR analytics scenario where leadership needs to understand:

What is driving employee attrition?

Which roles and departments are most at risk?

Can we proactively identify high-risk employees before they leave?

What strategic interventions can reduce preventable turnover?

The goal was not just to build a dashboard, but to:

Transform raw HR data into actionable insight

Build a predictive risk segmentation model

Deliver executive-level recommendations

Demonstrate end-to-end Power BI capability

✅ Did the Project Achieve Its Objective?

Yes — the analysis successfully:

Identified the top 3 drivers of attrition

Located role-level and department-level hotspots

Built a functional risk scoring model

Validated predictive segmentation (59 historical attrition cases were previously High Risk)

Delivered strategic, data-backed executive recommendations

The project moved from descriptive analytics (what happened) to diagnostic and prescriptive analytics (why it happened and what should be done).

🗂 Dataset Description

The dataset contains 1,470 employees with attributes including:

Demographics (Age, Gender, Marital Status, Education Field)

Job Information (Department, Job Role, Job Level)

Compensation (Monthly Income, Salary Hike)

Engagement Metrics (Job Satisfaction, Environment Satisfaction, Work-Life Balance)

Career Metrics (Years at Company, Years Since Last Promotion)

Operational Metrics (Overtime, Distance from Home)

Attrition (Yes/No)

A secondary table containing employee names was linked using Employee Number.

🧹 Data Cleaning & Transformation (Power Query)

All preprocessing was performed in Power Query Editor.

✔ Removed Irrelevant Columns

Standard Hours (constant)

Employee Count (constant)

✔ Data Type Standardization

Whole numbers for tenure, age, distance

Decimal for salary-related metrics

Text for categorical fields

✔ Created Derived Columns

Age Groups

Distance Buckets

Years Since Last Promotion Buckets

Tenure Buckets

✔ Removed Duplicates

Using:

Home → Remove Rows → Remove Duplicates

✔ Validated Data Integrity

Checked nulls

Validated table relationships

Confirmed no conflicting data types

🏗 Data Modeling

Built relationship between HR table and Employee table

Ensured correct cardinality (1-to-many)

Followed star-schema best practice

Controlled filter direction for accurate aggregation

📐 DAX Measures & Logic
Core KPIs
Total Employees
Total Employees = COUNT(HR[EmployeeNumber])

Total Attrition
Total Attrition =
CALCULATE(
    COUNT(HR[EmployeeNumber]),
    HR[Attrition] = "Yes"
)

Attrition Rate
Attrition Rate =
DIVIDE([Total Attrition], [Total Employees])

Driver Calculations

Used DAX functions such as:

CALCULATE()

DIVIDE()

COUNT()

IF()

SWITCH()

Example:

Overtime Attrition % =
DIVIDE(
    CALCULATE([Total Attrition], HR[OverTime] = "Yes"),
    [Total Attrition]
)

🎯 Risk Segmentation Model

A custom Risk Score was created using weighted logic:

Risk Score =
IF(HR[OverTime] = "Yes", 2, 0) +
IF(HR[JobSatisfaction] <= 2, 2, 0) +
IF(HR[YearsSinceLastPromotion] >= 5, 1, 0) +
IF(HR[WorkLifeBalance] <= 2, 1, 0)


Risk Categories:

Risk Category =
SWITCH(
    TRUE(),
    HR[Risk Score] >= 4, "High Risk",
    HR[Risk Score] >= 2, "Medium Risk",
    "Low Risk"
)

Result:

135 active employees identified as High Risk

59 historical attrition cases were classified High Risk

This validates predictive capability.
Key Findings

Overtime is the primary attrition driver (31.65%)

Job Satisfaction accounts for 27.85% of attrition

Early-career employees most vulnerable

Operational roles show highest attrition

Technical backgrounds (Life Sciences & Medical) overrepresented

Risk model successfully identifies at-risk workforce segments

🧠 Executive Recommendations

Implement overtime threshold monitoring in R&D and Sales.

Conduct department-level engagement diagnostics.

Formalize structured career roadmaps.

Strengthen onboarding & mentorship for early-tenure employees.

Introduce proactive stay interviews for High-Risk employees.
