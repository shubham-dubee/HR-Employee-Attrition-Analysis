# HR Employee Attrition Analysis

## Project Overview

This project analyzes employee attrition using **Excel** and **SQL**.
The main objective is to identify which employee groups have higher attrition rates and understand possible factors related to employee turnover.

The analysis focuses on:

* Department
* Job Role
* OverTime
* Age Group
* Marital Status
* Gender
* Monthly Income

---

## Dataset Overview

The dataset contains HR information for employees.

| Metric                 |  Value |
| ---------------------- | -----: |
| Total Employees        |  1,470 |
| Employees Left         |    237 |
| Active Employees       |  1,233 |
| Overall Attrition Rate | 16.12% |

### Key Columns Used

* Age
* Attrition
* Department
* JobRole
* Gender
* MaritalStatus
* MonthlyIncome
* OverTime
* EmployeeNumber

---

## Tools Used

* Microsoft Excel
* Pivot Tables
* Excel Charts
* SQL
* SQLite
* Google Colab

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

| KPI              |  Value |
| ---------------- | -----: |
| Total Employees  |  1,470 |
| Employees Left   |    237 |
| Active Employees |  1,233 |
| Attrition Rate   | 16.12% |

### Dashboard Charts

* Attrition Rate by Department
* Attrition Rate by Job Role
* Attrition Rate by OverTime
* Attrition Rate by Age Group
* Attrition Rate by Marital Status
* Attrition Rate by Gender

---

# SQL Analysis

The SQL analysis was performed using **SQLite in Google Colab**.

Table name used:

```sql
hr
```

---

## 1. Overall Attrition Count

### SQL Query

```sql
SELECT
    Attrition,
    COUNT(*) AS Employee_Count
FROM hr
GROUP BY Attrition;
```

### Result

| Attrition | Employee Count |
| --------- | -------------: |
| No        |           1233 |
| Yes       |            237 |

### Insight

The company has an overall attrition rate of **16.12%**.

---

## 2. Attrition Rate by Department

### SQL Query

```sql
SELECT
    Department,
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Employees_Left,
    ROUND(
        SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*),
        2
    ) AS Attrition_Rate
FROM hr
GROUP BY Department
ORDER BY Attrition_Rate DESC;
```

### Result

| Department             | Total Employees | Employees Left | Attrition Rate |
| ---------------------- | --------------: | -------------: | -------------: |
| Sales                  |             446 |             92 |         20.63% |
| Human Resources        |              63 |             12 |         19.05% |
| Research & Development |             961 |            133 |         13.84% |

### Insight

The **Sales department** has the highest attrition rate at **20.63%**.

Although Research & Development has the highest number of employees leaving, Sales has the highest attrition rate because department sizes are different.

---

## 3. Attrition Rate by Job Role

### SQL Query

```sql
SELECT
    JobRole,
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Employees_Left,
    ROUND(
        SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*),
        2
    ) AS Attrition_Rate
FROM hr
GROUP BY JobRole
ORDER BY Attrition_Rate DESC;
```

### Result

| Job Role              | Total Employees | Employees Left | Attrition Rate |
| --------------------- | --------------: | -------------: | -------------: |
| Sales Representative  |              83 |             33 |         39.76% |
| Laboratory Technician |             259 |             62 |         23.94% |
| Human Resources       |              52 |             12 |         23.08% |
| Sales Executive       |             326 |             57 |         17.48% |
| Research Scientist    |             292 |             47 |         16.10% |

### Insight

**Sales Representative** has the highest attrition rate at **39.76%**.

This means almost 4 out of every 10 Sales Representatives left the company.

---

## 4. Attrition Rate by OverTime

### SQL Query

```sql
SELECT
    OverTime,
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Employees_Left,
    ROUND(
        SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*),
        2
    ) AS Attrition_Rate
FROM hr
GROUP BY OverTime
ORDER BY Attrition_Rate DESC;
```

### Result

| OverTime | Total Employees | Employees Left | Attrition Rate |
| -------- | --------------: | -------------: | -------------: |
| Yes      |             416 |            127 |         30.53% |
| No       |            1054 |            110 |         10.44% |

### Insight

Employees working overtime have an attrition rate of **30.53%**, while employees not working overtime have an attrition rate of **10.44%**.

This shows that employees working overtime leave at almost **three times higher rate**.

---

## 5. Attrition Rate by Age Group

### SQL Query

```sql
SELECT
    CASE
        WHEN Age < 30 THEN 'Under 30'
        WHEN Age BETWEEN 30 AND 40 THEN '30-40'
        WHEN Age BETWEEN 41 AND 50 THEN '41-50'
        ELSE '50+'
    END AS Age_Group,

    COUNT(*) AS Total_Employees,

    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Employees_Left,

    ROUND(
        SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*),
        2
    ) AS Attrition_Rate

FROM hr
GROUP BY Age_Group
ORDER BY Attrition_Rate DESC;
```

### Result

| Age Group | Total Employees | Employees Left | Attrition Rate |
| --------- | --------------: | -------------: | -------------: |
| Under 30  |             326 |             91 |         27.91% |
| 30-40     |             679 |             94 |         13.84% |
| 50+       |             143 |             18 |         12.59% |
| 41-50     |             322 |             34 |         10.56% |

### Insight

Employees **under 30** have the highest attrition rate at **27.91%**.

This suggests younger employees may be more likely to leave the company.

---

## 6. Attrition Rate by Marital Status

### SQL Query

```sql
SELECT
    MaritalStatus,
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Employees_Left,
    ROUND(
        SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*),
        2
    ) AS Attrition_Rate
FROM hr
GROUP BY MaritalStatus
ORDER BY Attrition_Rate DESC;
```

### Result

| Marital Status | Total Employees | Employees Left | Attrition Rate |
| -------------- | --------------: | -------------: | -------------: |
| Single         |             470 |            120 |         25.53% |
| Married        |             673 |             84 |         12.48% |
| Divorced       |             327 |             33 |         10.09% |

### Insight

Single employees have the highest attrition rate at **25.53%**.

---

## 7. Attrition Rate by Gender

### SQL Query

```sql
SELECT
    Gender,
    COUNT(*) AS Total_Employees,
    SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Employees_Left,
    ROUND(
        SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*),
        2
    ) AS Attrition_Rate
FROM hr
GROUP BY Gender
ORDER BY Attrition_Rate DESC;
```

### Result

| Gender | Total Employees | Employees Left | Attrition Rate |
| ------ | --------------: | -------------: | -------------: |
| Male   |             882 |            150 |         17.01% |
| Female |             588 |             87 |         14.80% |

### Insight

Male employees have a slightly higher attrition rate than female employees.

However, the difference is not very large, so gender does not appear to be the strongest attrition driver.

---

## 8. Job Role Attrition Ranking

### SQL Query

```sql
WITH jobrole_attrition AS
(
    SELECT
        JobRole,
        COUNT(*) AS Total_Employees,
        SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Employees_Left,
        ROUND(
            SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*),
            2
        ) AS Attrition_Rate
    FROM hr
    GROUP BY JobRole
)

SELECT
    JobRole,
    Total_Employees,
    Employees_Left,
    Attrition_Rate,
    RANK() OVER(
        ORDER BY Attrition_Rate DESC
    ) AS Attrition_Rank
FROM jobrole_attrition;
```

### Result

| Attrition Rank | Job Role              | Attrition Rate |
| -------------: | --------------------- | -------------: |
|              1 | Sales Representative  |         39.76% |
|              2 | Laboratory Technician |         23.94% |
|              3 | Human Resources       |         23.08% |
|              4 | Sales Executive       |         17.48% |
|              5 | Research Scientist    |         16.10% |

### Insight

Sales Representative ranked first for attrition risk.

This query uses a CTE and the `RANK()` window function.

---

## 9. Department Attrition Ranking

### SQL Query

```sql
WITH department_attrition AS
(
    SELECT
        Department,
        COUNT(*) AS Total_Employees,
        SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Employees_Left,
        ROUND(
            SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*),
            2
        ) AS Attrition_Rate
    FROM hr
    GROUP BY Department
)

SELECT
    Department,
    Total_Employees,
    Employees_Left,
    Attrition_Rate,
    RANK() OVER(
        ORDER BY Attrition_Rate DESC
    ) AS Department_Rank
FROM department_attrition;
```

### Result

| Department Rank | Department             | Attrition Rate |
| --------------: | ---------------------- | -------------: |
|               1 | Sales                  |         20.63% |
|               2 | Human Resources        |         19.05% |
|               3 | Research & Development |         13.84% |

### Insight

Sales ranked first among departments for attrition risk.

---

## 10. Salary Ranking by Job Role

### SQL Query

```sql
WITH jobrole_salary AS
(
    SELECT
        JobRole,
        COUNT(*) AS Total_Employees,
        ROUND(AVG(MonthlyIncome),2) AS Avg_Monthly_Income
    FROM hr
    GROUP BY JobRole
)

SELECT
    JobRole,
    Total_Employees,
    Avg_Monthly_Income,
    RANK() OVER(
        ORDER BY Avg_Monthly_Income DESC
    ) AS Salary_Rank
FROM jobrole_salary;
```

### Result

| Salary Rank | Job Role                  | Avg Monthly Income |
| ----------: | ------------------------- | -----------------: |
|           1 | Manager                   |           17181.68 |
|           2 | Research Director         |           16033.55 |
|           3 | Healthcare Representative |            7528.76 |
|           4 | Manufacturing Director    |            7295.14 |
|           5 | Sales Executive           |            6924.28 |
|           9 | Sales Representative      |            2626.00 |

### Insight

Managers and Research Directors have the highest average monthly income.

Sales Representatives have the lowest average monthly income.

---

## 11. Combined Attrition and Salary Analysis

### SQL Query

```sql
WITH jobrole_summary AS
(
    SELECT
        JobRole,
        COUNT(*) AS Total_Employees,
        SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS Employees_Left,
        ROUND(
            SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*),
            2
        ) AS Attrition_Rate,
        ROUND(AVG(MonthlyIncome),2) AS Avg_Monthly_Income
    FROM hr
    GROUP BY JobRole
)

SELECT
    JobRole,
    Total_Employees,
    Employees_Left,
    Attrition_Rate,
    Avg_Monthly_Income,
    RANK() OVER(
        ORDER BY Attrition_Rate DESC
    ) AS Attrition_Rank,
    RANK() OVER(
        ORDER BY Avg_Monthly_Income DESC
    ) AS Salary_Rank
FROM jobrole_summary
ORDER BY Attrition_Rank;
```

### Result

| Job Role              | Attrition Rate | Avg Monthly Income | Attrition Rank | Salary Rank |
| --------------------- | -------------: | -----------------: | -------------: | ----------: |
| Sales Representative  |         39.76% |            2626.00 |              1 |           9 |
| Laboratory Technician |         23.94% |            3237.17 |              2 |           8 |
| Human Resources       |         23.08% |            4235.75 |              3 |           6 |
| Manager               |          4.90% |           17181.68 |              8 |           1 |
| Research Director     |          2.50% |           16033.55 |              9 |           2 |

### Insight

Sales Representative has the highest attrition rate and the lowest average monthly income among all job roles.

This suggests that compensation may be one possible factor related to higher attrition in this role.

---

# Key Findings

1. The overall attrition rate is **16.12%**.
2. The Sales department has the highest department-level attrition rate at **20.63%**.
3. Sales Representative has the highest job-role attrition rate at **39.76%**.
4. Employees working overtime have a much higher attrition rate at **30.53%**.
5. Employees under 30 have the highest age-group attrition rate at **27.91%**.
6. Single employees have the highest marital-status attrition rate at **25.53%**.
7. Sales Representative has the lowest average monthly income and the highest attrition rate.
8. Gender does not appear to be a major attrition driver compared to job role, overtime, and age group.

---

# Business Recommendations

1. Review overtime policies because employees working overtime show much higher attrition.
2. Focus retention efforts on Sales Representatives and Laboratory Technicians.
3. Investigate compensation structure for Sales Representative roles.
4. Create retention programs for employees under 30.
5. Conduct employee feedback surveys in high-risk departments and job roles.
6. Improve career growth and engagement programs for early-career employees.
7. Monitor Sales department attrition closely because it has the highest department-level attrition rate.

---

# Skills Demonstrated

* Excel Pivot Tables
* Excel Dashboarding
* SQL Aggregations
* `CASE WHEN`
* `GROUP BY`
* CTEs
* Window Functions
* `RANK()`
* Business Insight Generation
* HR Analytics

---

# Project Files

* `HR_Attrition_Analysis_Final.xlsx`
* `HR_Attrition_SQL_Analysis.ipynb`
* `HR_Employee_Attrition_Analysis_Report.docx`
* `HR_Employee_Attrition_Analysis_Report.pdf`
* `README.md`

---

# Project Conclusion

This HR Employee Attrition Analysis project identified major employee groups with higher attrition risk.

The strongest attrition factors found were job role, overtime, age group, marital status, and compensation level.

Sales Representatives were the highest-risk group, with the highest attrition rate and the lowest average monthly income. Employees working overtime and employees under 30 also showed significantly higher attrition rates.

This project demonstrates how Excel and SQL can be used together to analyze HR data and generate actionable business recommendations.
