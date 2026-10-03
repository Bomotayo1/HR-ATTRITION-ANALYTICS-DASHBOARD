## HR-ATTRITION-ANALYTICS-DASHBOARD

An end-to-end HR analytics project built in Microsoft Excel, using Power Query for data cleaning and PivotTables/PivotCharts
for analysis and visualization. The goal was to identify where and why employee attrition is happening and turn raw HR records into a decision-ready dashboard for management.

## Table of Contents
 - [Key Performance Indicators](#Key-Performance-Indicators)
 - [Business Questions](#Business-Questions)
 - [Tools Used](#Tools-Used)
 - [Data Cleaning Process (Power Query)](#Data-Cleaning-Process-Power-Query)
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
 - **Standardized date formats** across DOB, DateofHire, and LastPerformanceReview_Date, which mixed real date values with text-formatted dates
 - **Removed 10 redundant numeric ID columns** (GenderID, MaritalStatusID, MarriedID, FromDiversityJobFairID, Termd, EmpStatusID, DeptID, PositionID, PerfScoreID, ManagerID) that duplicated existing text columns
 - **Recoded the TermReason Column** from 18 raw, inconsistent text values into 8 clean categories (e.g., "Another Position", "Career change", and "retiring" were consolidated into
   Voluntary-Career Growth). Two entries in the raw data contained non-standard text and were recategorised as Other/Unspecified
 - **Added derived columns:** Age, Tenure_years,  TerminationYear, and Salary_Range, calculated using Power Query's M formula Language so they update automatically on refresh
## Dashboard
   [View Dashboard Screenshot](Dashboard/Screenshot%202026-10-02%20102707.png)
  
 The dashboard includes:

  - **KPI summary row:** Total Headcount, Overall Attrition Rate, Average Age, Average Tenure
  - **Department Filter Slicer** for interactive drill-down
  - **Attrition Rate by Department** (horizontal bar, % of each department that has left)
  - **Why Production Employees Leave** (breakdown of departure reasons in the highest-attrition department)
  - **Recruitment Source** (hires by channel)
  - **Employee Distribution by Salary Range**
  - **Key Insight callout** summarizing the engagement vs. satisfaction finding
## Key Findings

   1. **Overall attrition is 33%**, **and it's overwhelmingly voluntary.** Of 311 employees, 67% are active, 28% voluntarily left, and 5% were terminated for cause.
   2. **Production is the Primary driver of attrition - and the finding holds up at scale.** Production (209 employees, the company's largest department) has a 39.7% attrition rate
      (35.9% voluntary, 3.8% for cause). Software Engineering shows a similar percentage (36.4%), but with only 11 employees, which shows that the number should be treated cautiously.
   3. **Pay isn't the main reason people leave production - career growth is**

|  Reason  |  Count | % of Departures |
|----------|--------|-----------------|
| Career Growth | 27 | 32.5% |
| Dissatisfacttion | 20 | 24.1% |
| Personal | 16 | 19.3% |
| Compensation | 11 | 13.3% |
| Attendance (involuntary) | 6 | 7.2% |
| Performance/Conduct (involuntary) | 3 | 3.6% |

Compensation was the least-cited Voluntary reason, contrary to the common assumption that pay drives attrition.
