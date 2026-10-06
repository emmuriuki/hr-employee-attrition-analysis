# hr-employee-attrition-analysis

## 📌 Project Overview
This project analyzes employee attrition using HR employee data to understand workforce patterns, employee satisfaction, performance, workload, and departmental trends.

The analysis was developed using Microsoft Power BI to transform raw HR data into interactive visualizations and actionable business insights.

## 🎯 Business Problem
Employee attrition can affect organizational performance, productivity, workforce stability, and recruitment costs.

The objective of this analysis is to identify patterns associated with employee attrition and understand how factors such as satisfaction, performance, workload, tenure, promotion, salary, and department relate to employee retention.

## ❓ Business Questions
1. What is the overall employee attrition rate?
2. How does employee satisfaction relate to attrition?
3. Which departments have the highest attrition?
4. Does employee satisfaction relate to attrition?
5. Does workload relate to employee attrition?
6. Does promotion relate to employee retention?
7. Does salary level relate to attrition?
8. How does employee performance vary across departments?

## 📊 Dataset
The dataset contains 14,999 employee records and 11 variables: employee ID, satisfaction level, last evaluation, number of projects, average monthly hours, years at company, work accident, left, promotion in last 5 years, department and salary.

**Data source:** Kaggle, HR_Employee_Data (`data/HR_Employee_Data_raw.xlsx`)

## 🛠️ Tools & Technologies
Microsoft Power BI, Power Query, DAX, Microsoft Excel, Kaggle, GitHub

## 🧹 Data Cleaning (Power Query)
- 14,999 rows, 0 nulls, 0 duplicate rows, 0 duplicate Employee IDs. No rows removed or imputed.
- Fixed the `average_montly_hours` typo and renamed all columns to Title_Case.
- Standardised department labels (`RandD` to R&D, `product_mng` to Product Management, `hr` to HR) and salary labels.
- 337 Employee IDs have fewer than 5 digits; they are unique and were kept as supplied.
- Added: Attrition_Status, Promotion_Status, Work_Accident_Status, Satisfaction_Band, Performance_Band, Hours_Band, Tenure_Band.

Files: `powerbi/PowerQuery_M.pq`, `data/HR_Employee_Data_Clean.csv

## 🧱 Data Model
 Descriptive and diagnostic workforce analysis in Power BI using DAX measures and comparative visuals. No predictive model was developed; the objective was to identify decision-useful workforce patterns.

## 🧮 DAX Measures
Core: Total Employees, Employees Left, Attrition Rate, Retention Rate. Averages: satisfaction (overall, left, stayed), evaluation, monthly hours, projects, tenure. Comparison: Company Attrition Rate, Attrition vs Company, % of All Leavers, Department Attrition Rank. All in `powerbi/DAX_Measures.dax`.

```dax
Attrition Rate = DIVIDE ( [Employees Left], [Total Employees], 0 )
Employees Left = CALCULATE ( [Total Employees], HR_Employee[Left_Flag] = 1 )
```

## 📈 Dashboard
Layout and formatting spec: `documentation/Dashboard_Layout.md`. Interactive preview: `powerbi/HR_Attrition_Dashboard.html` (department, salary and promotion filters). Screenshot: `screenshots/dashboard_overview.png`.

## 🔍 Analysis and Answers

| # | Question | Answer |
|---|---|---|
| 1 | Overall attrition | 3,571 of 14,999 employees left: **23.8%** |
| 2 | Satisfaction bands | 0.0-0.2: 62.5%, 0.2-0.4: 49.3%, 0.4-0.6: 24.0%, 0.6-0.8: 9.9%, 0.8-1.0: 13.7% |
| 3 | Departments | HR 29.1%, Accounting 26.6%, Technical 25.6%, Support 24.9%, Sales 24.5%, Marketing 23.7%, IT 22.2%, Product Mgmt 22.0%, R&D 15.4%, Management 14.4% |
| 4 | Avg satisfaction | Left 0.44 vs stayed 0.67 |
| 5 | Workload | 2 projects 65.6%, 3: 1.8%, 4: 9.4%, 5: 22.2%, 6: 55.8%, 7: 100% (256 of 256). Hours: <=150 35.6%, 151-200 12.7%, 201-250 15.8%, >250 38.8% |
| 6 | Promotion | Promoted 6.0% (19 of 319) vs not promoted 24.2% |
| 7 | Salary | Low 29.7%, medium 20.4%, high 6.6% |
| 8 | Performance by department | Average evaluation is 0.71 to 0.72 in all ten departments |

## 💡 Key Insights
1. **Roughly one in four employees left (23.8%).**
2. **Low satisfaction is the strongest signal.** Leavers averaged 0.44 vs 0.67. The 0.8-1.0 band (13.7%) is higher than 0.6-0.8 (9.9%), so some highly satisfied employees also leave.
3. **Workload has a U shape.** Under-loaded (2 projects) and over-loaded (6 to 7 projects) staff leave most; 3 to 4 projects is the lowest-risk zone. Every employee with 7 projects left.
4. **Both very low and very high hours go with attrition** (35.6% at 150 hours or less, 38.8% above 250).
5. **Attrition peaks at year 5 (56.6%)**, then drops. Nobody with 7+ years left; 2-year employees rarely leave (1.6%).
6. **Departments differ modestly.** HR, Accounting and Technical are highest; Management and R&D are lowest. The spread (14.4% to 29.1%) is smaller than the spread by satisfaction, projects or salary.
7. **Promotion and retention go together, but promotion is rare.** Only 2.1% were promoted in 5 years.
8. **Pay level matters.** Low-salary staff are 49% of headcount but 61% of leavers.
9. **Performance does not differ by department**, and top performers are not safe: 30.8% of high-rated employees (above 0.80) left, vs 5.8% of mid-rated.
10. Employees with a work accident left less (7.8% vs 26.5%).

These are associations in a snapshot dataset, not proof of cause.

## 🎯 Recommendations
1. Prioritize satisfaction: Run targeted engagement analysis in high-attrition departments and identify the specific drivers of dissatisfaction.
2. Strengthen career progression: Improve promotion transparency, internal mobility, mentoring and skills-development pathways.
3. Review lower salary bands: Assess compensation competitiveness and combine pay reviews with recognition and career opportunities.
4. Monitor workload: Track monthly hours, project allocation and workload concentration, especially in high-attrition teams.
5. Focus department interventions: Prioritize HR and Sales while investigating retention practices in R&D and Management.
6. Establish ongoing monitoring: Refresh the Power BI dashboard regularly and track attrition, satisfaction, promotion and workload indicators.

## 📁 Project Structure
```
hr-employee-attrition-analysis/
├── README.md
├── data/            raw xlsx, clean xlsx
├── powerbi/         PowerQuery_M.pq, DAX_Measures.dax, HR_Attrition_Dashboard.html
├── screenshots/     dashboard_overview.png
└── documentation/   Dashboard_Layout.md
```
The `.pbix` file is built by following the files in xlsx format, MNC company HR data

## 👩🏾‍💻 Author
**Evah Muriuki**
Data Analyst 
Skills: Excel | SQL | Power BI | Python

This project is part of my ongoing Data Analytics portfolio.
