# HR Employee Analytics

## Project Overview

HR Employee Analytics is a data analysis and business intelligence project focused on understanding employee demographics, salaries, performance, workforce distribution, and employee attrition.

The project uses Python for data cleaning, validation, exploratory data analysis (EDA), and business analysis, followed by Power BI for KPI reporting and data visualization.

## Dataset

- Dataset: HR Employee Dataset — Indian Corporate Workforce
- Records: 1,000 employees
- Original columns: 14
- Final columns after analysis: 15
- Geographic coverage: Indian cities
- Salary currency: INR
- Dataset type: Synthetic/Fictional HR dataset

### Key Data Fields

- Employee ID
- Age
- Gender
- City
- Education
- Department
- Job Title
- Join Date
- Years at Company
- Salary
- Performance Rating
- Leaves Taken
- Employment Status
- Age Group

## Tools & Technologies

- Python
- Pandas
- Google Colab
- Power BI
- DAX
- Data Cleaning
- Exploratory Data Analysis (EDA)
- Data Visualization

## Project Workflow

Raw Dataset
↓
Data Inspection
↓
Data Quality Checks
↓
Data Cleaning
↓
Missing Value Treatment
↓
Data Validation
↓
Exploratory Data Analysis
↓
Business Analysis
↓
Cleaned Dataset
↓
Power BI Dashboard
↓
KPI Reporting & Visualization

## Python Data Preparation

The dataset was inspected and validated using Python and Pandas.

### Data Quality Checks

- Checked dataset dimensions and column names
- Checked missing values
- Checked duplicate records
- Checked unique Employee IDs
- Checked data types
- Validated salary values
- Validated age values
- Validated years at company
- Validated leaves taken
- Checked categorical consistency
- Converted Join_Date to datetime format

### Missing Value Treatment

The dataset contained missing values in:

- Salary_INR
- Performance_Rating

Missing salary values were replaced using the median salary.

Missing performance ratings were replaced using the mode.

After treatment, all missing values were successfully handled.

### Feature Engineering

An Age_Group column was created to classify employees into:

- 21-30
- 31-40
- 41-50
- 51-60

## Exploratory Data Analysis

The analysis examined relationships between:

- Department and employee count
- Department and salary
- Job title and salary
- Education and salary
- City and salary
- Employment status and salary
- Department and attrition
- Performance rating and attrition
- Tenure and attrition
- Age group and attrition
- Performance rating and salary
- Department and performance
- Department and leaves taken
- City and employment status
- Gender and employment status

## Key Insights

### Workforce Distribution

Operations had the highest number of employees, while HR had the lowest number among the departments.

### Salary by Department

Engineering had the highest average salary, while Customer Support had the lowest average salary.

### Salary by Job Title

QA Engineer had the highest average salary among the job titles in the dataset.

### Attrition by Department

Engineering had the highest department-level attrition rate at approximately 38.3%, followed closely by Sales at approximately 38.2%.

Operations had the lowest attrition rate at approximately 31.6%.

### Performance and Attrition

Employees with an Excellent performance rating had the lowest attrition rate, while employees with an Average rating had the highest.

These results represent associations observed in the dataset and do not establish causation.

### Age and Attrition

Attrition increased across the age groups in this dataset.

The 51-60 age group had the highest attrition rate at approximately 39.5%, while the 21-30 group had the lowest at approximately 32.6%.

### Salary and Education

Average salaries across education levels were relatively similar, indicating that education level did not show a strong salary difference in this dataset.

### City and Salary

Average salaries across the seven cities were relatively close, suggesting that city was not a major differentiating factor for salary in this dataset.

## Power BI Dashboard

The Power BI dashboard includes the following KPI cards:

- Total Employees
- Average Salary
- Average Years at Company
- Average Leaves Taken

### Dashboard Visualizations

- Employee Count by Department
- Employment Status Distribution
- Average Salary by Department
- Attrition Rate by Department
- Performance Rating Distribution
- Attrition Rate by Age Group
- Average Salary by Performance Rating
- Employee Count by City
- Average Salary by Job Title

## DAX Measure

The following DAX measure was created to calculate the overall attrition rate:

```DAX
Attrition Rate =
DIVIDE(
    CALCULATE(
        COUNTROWS('HR_Employee_Analytics_Cleaned'),
        'HR_Employee_Analytics_Cleaned'[Employment_Status] <> "Active"
    ),
    COUNTROWS('HR_Employee_Analytics_Cleaned')
)