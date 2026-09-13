# Project Documentation — HR Employee Analytics

## 1. Project Objective

The objective of this project is to analyze employee data and identify useful patterns related to workforce distribution, salary, performance, employee leaves, and attrition.

The project demonstrates an end-to-end data analytics workflow using Python for data preparation and analysis and Power BI for business intelligence reporting and visualization.

---

## 2. Dataset Information

The project uses the HR Employee Dataset — Indian Corporate Workforce.

- Number of employees: 1,000
- Original columns: 14
- Final columns: 15
- Dataset type: Synthetic/Fictional
- Salary currency: INR
- Cities represented: 7
- Departments represented: 7

The dataset contains employee-level information including age, gender, city, education, department, job title, joining date, years at company, salary, performance rating, leaves taken, and employment status.

---

## 3. Data Preparation

Python and Pandas were used to inspect, clean, validate, and prepare the dataset.

### Data Inspection

The following checks were performed:

- Dataset shape and column names
- Data types
- Missing values
- Duplicate records
- Unique Employee IDs
- Categorical value consistency
- Numeric value validity

### Data Quality Results

- Total records: 1,000
- Duplicate rows: 0
- Unique Employee IDs: 1,000
- Missing Salary values: 32
- Missing Performance Rating values: 19

Numeric fields were checked for invalid values. No invalid salary, age, years-at-company, or leaves-taken values were identified based on the validation ranges used during the analysis.

---

## 4. Missing Value Treatment

### Salary

Missing Salary_INR values were replaced using the median salary of the dataset.

Median salary before imputation: ₹67,250.

### Performance Rating

Missing Performance_Rating values were replaced using the most frequently occurring performance rating (mode).

After imputation, the dataset contained no missing values.

---

## 5. Feature Engineering

An Age_Group column was created using the employee's age.

The groups were:

- 21-30
- 31-40
- 41-50
- 51-60

This feature was used to analyze employee attrition across different age groups.

---

## 6. Exploratory Data Analysis

The following areas were analyzed:

### Workforce

- Employee count by department
- Employee count by city
- Employment status distribution
- Gender distribution
- Education distribution

### Salary

- Average salary by department
- Average salary by job title
- Average salary by education
- Average salary by city
- Average salary by employment status
- Average salary by performance rating
- Average salary by years at company

### Attrition

Attrition was analyzed by:

- Department
- Performance rating
- Age group
- Years at company
- Gender
- City

### Other Analysis

- Leaves taken by employment status
- Age by employment status
- Department performance distribution

---

## 7. Attrition Definition

For this project, employees whose Employment_Status was not "Active" were treated as attrited employees.

Therefore:

Attrition = Resigned + Terminated

Attrition Rate was calculated as:

Attrition Rate = Non-Active Employees / Total Employees

This definition was used consistently in the Python analysis and Power BI dashboard.

---

## 8. Key Analysis Findings

### Salary by Department

Engineering had the highest average salary at approximately ₹107,484.

Customer Support had the lowest average salary at approximately ₹49,149.

### Attrition by Department

Engineering had the highest attrition rate at approximately 38.3%.

Sales followed closely at approximately 38.2%.

Operations had the lowest attrition rate at approximately 31.6%.

### Performance and Attrition

The observed attrition rates were:

- Excellent: approximately 32.6%
- Good: approximately 35.6%
- Average: approximately 37.2%
- Poor: approximately 35.3%

These are associations observed in the dataset and should not be interpreted as proof that performance causes attrition.

### Age Group and Attrition

The observed attrition rates increased across the age groups:

- 21-30: approximately 32.6%
- 31-40: approximately 34.1%
- 41-50: approximately 36.1%
- 51-60: approximately 39.5%

The 51-60 group had the highest observed attrition rate.

### Education and Salary

Average salaries across education levels were relatively similar, so the dataset did not show a strong salary difference based on education level.

### City and Salary

Average salaries across the seven cities were relatively close, indicating that city did not show a major salary difference in this dataset.

---

## 9. Power BI Dashboard

The cleaned dataset was imported into Power BI.

The dashboard contains four main KPI cards:

1. Total Employees
2. Average Salary
3. Average Years at Company
4. Average Leaves Taken

The dashboard also contains visualizations for:

- Employee Count by Department
- Employment Status Distribution
- Average Salary by Department
- Attrition Rate by Department
- Performance Rating Distribution
- Attrition Rate by Age Group
- Average Salary by Performance Rating
- Employee Count by City
- Average Salary by Job Title

---

## 10. DAX Measure

The following DAX measure was created in Power BI:

```DAX
Attrition Rate =
DIVIDE(
    CALCULATE(
        COUNTROWS('HR_Employee_Analytics_Cleaned'),
        'HR_Employee_Analytics_Cleaned'[Employment_Status] <> "Active"
    ),
    COUNTROWS('HR_Employee_Analytics_Cleaned')
)