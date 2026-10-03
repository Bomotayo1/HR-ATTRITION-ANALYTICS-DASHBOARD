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

 4. **Engagement and satisfaction tell different stories depending on why someone left**.
    
     | Group | Avg. satisfaction | Avg. Engagement |
     |-------|-------------------|-----------------|
     | Active | 4.00 | 4.12 |
     | Terminated for Cause | 5.00 | 2.10 |
     | Voluntarily Terminated | 4.00 | 4.58 |

     Voluntarily terminated employees reported higher engagement (4.58) than active employees (4.12). Employees terminated for cause show a contradiction:
     The highest self-reported satisfaction (5.00) paired with the lowest engagement (2.10) of any group - based on a small sample of 16 employees.
5. **Indeed and Linkedin are dominant recruitment channels**. The majority of hires came through these two sources, with smaller contributions from Google Search, employee referrals, and diversity job fairs.
   ## Recommendations

    1. **Prioritize retention efforts in production**. As the largest department with the highest-volume attrition, even small improvements here will have an outsized impact on overall attrition rate.
    2. **Build clearer internal advancement paths**. Since career growth is the top reason for voluntary departure, employees may be leaving for opportunities the company could offer internally.
    3. **Investigate day-to-day dissatisfaction drivers in production.** Dissatisfaction is the #2 reason for leaving; this dataset doesn't capture why, so exit interviews or a targeted survey would help
       clarify whether it's workload, management, or recognition-related.
    4. **Treat compensation adjustments as a lower-priority lever** for production specifically, since it was the least-cited voluntary reason-resources may be better
          spent on growth and dissatisfaction drivers.
    5. **Review satisfaction survey design.** The gap between high self-reported satisfaction and low engagement among for-cause terminations suggests the survey
           may not be capturing behavioral or performance warning signs - worth pairing survey data with manager check-ins.
    6. **Continue investing in Indeed and LinkedIn** as primary recruitment channels, given their disproportionate share of successful hires.

  ## How to Use This File
   1. Download [HRDataset_V15_Data](Data/HRDataset_v15.xlsx.xlsx)
   2. Open it in Microsoft Excel (recommended: Excel 2016 or later for full PivotTable/slicer support).
   3. Go to the **Dashboard** tab to view the finished visualizations.
   4. Use the **Department slicer** at the top of the dashboard to filter all connected charts by department.
   5. To review the underlying cleaning logic, open **Power Query Editor** (Data tab > Queries & Connections > right-click the query > Edit) to see the full list of applied steps.
## Limitations
   - Several departments (Admin Offices: 9 people, Software Engineering: 11 people, Executive Office: 1 person) are too small for their attrition percentages to be treated as strongly
     conclusive; they're reported for completeness, but production's findings carry more statistical weight given its size.
   - This dataset does not capture exit-interview detail, so while engagement and satisfaction scores are suggestive, they are not proof of causation.
   - All cleaning and derived columns (Age, Tenure, Termination Year, Salary_Range) were built using powerquery and can be fully audited via the Applied Steps panel in the source file.

## Related project
   This analysis pairs with a SQL-based exploration of a separate retail dataset (Kultra Mega Stores), demonstrating the same end-to-end analytical process - Business question, cleaning, analysis, insight-across 
    two different tools and domains.
    [link to SQL repo]()

## Contact
**BABATUNDE OMOTAYO** | [Linkedin](www.linkedin.com/in/omotayo-babatunde) | [Gmail](mailto:bomotayo99@gmail.com)
