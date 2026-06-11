# HR Employee Attrition Analysis

## Project Overview

This project analyzes employee attrition using Excel and SQL.  
The goal is to identify which employee groups have higher attrition rates and understand possible factors related to employee turnover.

The analysis focuses on department, job role, overtime, age group, marital status, gender, and monthly income.

---

## Dataset Overview

| Metric | Value |
|---|---:|
| Total Employees | 1,470 |
| Employees Left | 237 |
| Active Employees | 1,233 |
| Overall Attrition Rate | 16.12% |

### Key Columns Used

- Age
- Attrition
- Department
- JobRole
- Gender
- MaritalStatus
- MonthlyIncome
- OverTime
- EmployeeNumber

---

## Tools Used

- Microsoft Excel
- Pivot Tables
- Excel Charts
- SQL
- SQLite
- Google Colab

---

## Business Questions

1. What is the overall employee attrition rate?
2. Which department has the highest attrition rate?
3. Which job role has the highest attrition rate?
4. Are employees working overtime more likely to leave?
5. Which age group has the highest attrition?
6. Does marital status affect attrition?
7. Is attrition different between male and female employees?
8. Which job roles have high attrition and low average income?

---

## Excel Dashboard

The Excel dashboard was created using Pivot Tables and charts.

### Dashboard KPIs

| KPI | Value |
|---|---:|
| Total Employees | 1,470 |
| Employees Left | 237 |
| Active Employees | 1,233 |
| Attrition Rate | 16.12% |

### Dashboard Charts

- Attrition Rate by Department
- Attrition Rate by Job Role
- Attrition Rate by OverTime
- Attrition Rate by Age Group
- Attrition Rate by Marital Status
- Attrition Rate by Gender

---

## SQL Analysis

SQL analysis was performed using SQLite in Google Colab.

The main SQL techniques used were:

- GROUP BY
- CASE WHEN
- COUNT()
- SUM()
- AVG()
- ROUND()
- CTEs
- RANK() window function

---

## Key SQL Insights

### 1. Overall Attrition

| Attrition | Employee Count |
|---|---:|
| No | 1,233 |
| Yes | 237 |

**Insight:**  
The company has an overall attrition rate of 16.12%.

---

### 2. Attrition by Department

| Department | Total Employees | Employees Left | Attrition Rate |
|---|---:|---:|---:|
| Sales | 446 | 92 | 20.63% |
| Human Resources | 63 | 12 | 19.05% |
| Research & Development | 961 | 133 | 13.84% |

**Insight:**  
Sales has the highest department-level attrition rate at 20.63%.

---

### 3. Attrition by Job Role

| Job Role | Total Employees | Employees Left | Attrition Rate |
|---|---:|---:|---:|
| Sales Representative | 83 | 33 | 39.76% |
| Laboratory Technician | 259 | 62 | 23.94% |
| Human Resources | 52 | 12 | 23.08% |
| Sales Executive | 326 | 57 | 17.48% |
| Research Scientist | 292 | 47 | 16.10% |

**Insight:**  
Sales Representative has the highest attrition rate at 39.76%.

---

### 4. Attrition by OverTime

| OverTime | Total Employees | Employees Left | Attrition Rate |
|---|---:|---:|---:|
| Yes | 416 | 127 | 30.53% |
| No | 1,054 | 110 | 10.44% |

**Insight:**  
Employees working overtime have almost three times higher attrition than employees not working overtime.

---

### 5. Attrition by Age Group

| Age Group | Total Employees | Employees Left | Attrition Rate |
|---|---:|---:|---:|
| Under 30 | 326 | 91 | 27.91% |
| 30-40 | 679 | 94 | 13.84% |
| 50+ | 143 | 18 | 12.59% |
| 41-50 | 322 | 34 | 10.56% |

**Insight:**  
Employees under 30 have the highest age-group attrition rate at 27.91%.

---

### 6. Attrition by Marital Status

| Marital Status | Total Employees | Employees Left | Attrition Rate |
|---|---:|---:|---:|
| Single | 470 | 120 | 25.53% |
| Married | 673 | 84 | 12.48% |
| Divorced | 327 | 33 | 10.09% |

**Insight:**  
Single employees have the highest attrition rate at 25.53%.

---

### 7. Attrition by Gender

| Gender | Total Employees | Employees Left | Attrition Rate |
|---|---:|---:|---:|
| Male | 882 | 150 | 17.01% |
| Female | 588 | 87 | 14.80% |

**Insight:**  
Male employees have a slightly higher attrition rate, but the difference is not very large.

---

## Advanced SQL Analysis

### Job Role Attrition and Salary Ranking

| Job Role | Attrition Rate | Avg Monthly Income | Attrition Rank | Salary Rank |
|---|---:|---:|---:|---:|
| Sales Representative | 39.76% | 2,626.00 | 1 | 9 |
| Laboratory Technician | 23.94% | 3,237.17 | 2 | 8 |
| Human Resources | 23.08% | 4,235.75 | 3 | 6 |
| Manager | 4.90% | 17,181.68 | 8 | 1 |
| Research Director | 2.50% | 16,033.55 | 9 | 2 |

**Insight:**  
Sales Representative has the highest attrition rate and the lowest average monthly income among all job roles. This suggests compensation may be one possible factor related to higher attrition in this role.

---

## Key Findings

1. Overall attrition rate is 16.12%.
2. Sales department has the highest department-level attrition rate.
3. Sales Representative has the highest job-role attrition rate.
4. Employees working overtime have much higher attrition.
5. Employees under 30 have the highest age-group attrition.
6. Single employees have the highest marital-status attrition.
7. Sales Representative has both the highest attrition rate and the lowest average monthly income.
8. Gender does not appear to be a major attrition driver compared to job role, overtime, and age group.

---

## Business Recommendations

1. Review overtime policies because overtime employees show much higher attrition.
2. Focus retention efforts on Sales Representatives and Laboratory Technicians.
3. Investigate compensation structure for Sales Representative roles.
4. Create retention programs for employees under 30.
5. Conduct employee feedback surveys in high-risk departments and job roles.
6. Improve career growth and engagement programs for early-career employees.
7. Monitor Sales department attrition closely.

---

## Skills Demonstrated

- Excel Pivot Tables
- Excel Dashboarding
- SQL Aggregations
- CASE WHEN
- GROUP BY
- CTEs
- Window Functions
- RANK()
- HR Analytics
- Business Insight Generation

---

## Project Files

- HR_Attrition_Analysis_Final.xlsx
- HR_Attrition_SQL_Analysis.ipynb
- HR_Employee_Attrition_Analysis_Report.docx
- HR_Employee_Attrition_Analysis_Report.pdf
- README.md

---

## Project Conclusion

This HR Employee Attrition Analysis project identified major employee groups with higher attrition risk.

The strongest attrition factors found were job role, overtime, age group, marital status, and compensation level.

Sales Representatives were the highest-risk group, with the highest attrition rate and the lowest average monthly income. Employees working overtime and employees under 30 also showed significantly higher attrition rates.

This project demonstrates how Excel and SQL can be used together to analyze HR data and generate actionable business recommendations.
