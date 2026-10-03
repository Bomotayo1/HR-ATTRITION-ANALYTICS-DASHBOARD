## HR-ATTRITION-ANALYTICS-DASHBOARD

An end-to-end HR analytics project built in Microsoft Excel, using Power Query for data cleaning and PivotTables/PivotCharts
for analysis and visualization. The goal was to identify where and why employee attrition is happening and turn raw HR records into a decision-ready dashboard for management.

## Table of Contents
 - [Key Performance Indicators](#Key-Performance-Indicators)
 - [Business Questions](#Business-Questions)
 - [Tools Used](#Tools-Used)
 - [Data Cleaning Process (Power Query)](#DataCleaningProcess (Power-Query))
 - [Dashboard](#Dashboard)
 - [Key Findings](#Key-Findings)
 - [Recommendations](#Recommendations)
 - [How to use this file](#How-to-use-this-file)
 - [Repository Structure](#Repository-Structure)
 - [Limitations](#Limitations)
 - [Related Project](#Related-Projects)
 - [Contact](#Contacts)

## Key Performance Indicators

|  KPI    |     Result |
|------|---------|
| Total Employees | 311 |
| Overall Attrition Rate | 33% |
| Average Age | 47.2 |
| Average Tenure | 9.3 years |
| Active Employees | 67% |
| Voluntarily Terminated | 28% |
| Terminated for Cause | 5% |

## Business Questions
 1. What is the company's Overall attrition rate?
 2. Which department has the highest attrition and is that rate statistically meaningful given department size?
 3. What are the top reasons employees voluntarily leave?
 4. Which recruitment sources produce the most hires?
 5. How is the workforce distributed across salary brackets?
 6. Does employee engagement  or satisfaction relate to who stays and who leaves?
## Tools Used
 - Microsoft Excel
 - Power Query (data Cleaning and transformation)
 - PivotTables & PivotCharts
 - slicers (interactive filtering)
## Data Cleaning Process (Power Query)
The raw dataset (312 employees, 36 columns) required substantial cleaning before analysis:

 - **Trimmed and standardized text fields** (e.g., the Sex column contained hidden trailing spaces; HispanicLatino had inconsistent casing like
   "Yes"/"Yes"/"No"/"no")
