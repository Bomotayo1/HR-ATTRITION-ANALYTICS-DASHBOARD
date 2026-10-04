## Power Query Cleaning Steps

This document lists every transformation applied to the raw HRDataset_v15 data in Power Query, in the order they were applied (matching the "Applied Steps" panel in the Power Query Editor). The raw dataset started with 311 rows and 36 columns.

### **1. Load the Data**
     
  - Loaded the raw table into Power Query via **Data > From Table/Range**.

### **2. Trim and Clean Text Columns**
      
   - Applied **Transform > Format > Trim and Transform > Format > Clean** across all text columns (e.g., Sex, Position, Department, HispanicLatino).
   - This removed hidden leading/trailing spaces — for example, the Sex column originally contained values like "M " with a trailing space, which would otherwise cause COUNTIFS/PivotTable grouping errors.
### 3. Standardize Casing
   
  - Applied **Transform > Format > lowercase, followed by Transform > Format > Capitalize Each Word**, to the HispanicLatino column.
  -   This resolved inconsistent entries such as "Yes", "yes", "No", "no" all appearing as separate values.
### 4. Fix Date Columns

- Changed the data type of DOB, DateofHire, and LastPerformanceReview_Date to **Date**.
- These columns originally mixed true date values with text-formatted dates, which would have broken any date-based calculations (Age, Tenure) if left unresolved.
### 5. Remove Duplicate Rows
- Right-clicked the EmpID column header > **Remove Duplicates**, keeping the first occurrence of each employee ID.
### 6. Recode TermReason into TermReason_Category
- Added a new column, TermReason_Category, consolidating 18 raw, inconsistent TermReason values into 8 clean categories.
- Built using **Add Column > Conditional Column**, matching each raw value to its category. During this step, two raw values (Unhappy and medical issues) were initially missed due to case-sensitivity in the exact-match comparison and were corrected by matching the exact casing present in the source data.
- Mapping used:

|    Raw Value(s)	|    Category   |
|-----------------|---------------|
| N/A-StillEmployed |	Not Terminated|
|  Another position, career change, retiring |	Voluntary - Career Growth |
more money	| Voluntary - Compensation |
Unhappy, hours	| Voluntary - Dissatisfaction |
return to school, relocation out of area, maternity leave - did not return, medical issues, military	| Voluntary - Personal |
attendance, no-call no-show	| Involuntary - Attendance |
performance, gross misconduct	| Involuntary - Performance/Conduct |
Learned that he is a gangster, Fatal attraction	| Other/Unspecified |

Note: The two entries mapped to "Other/Unspecified" were non-standard/placeholder text present in the original public dataset and were recategorized rather than left miscoded.

### 7. Remove Redundant ID Columns
- Removed the following columns, each of which duplicated an existing text column:
     - GenderID (duplicate of Sex)
     - MaritalStatusID (duplicate of MaritalDesc)
     - MarriedID (duplicate of MaritalDesc)
     - EmpStatusID (duplicate of EmploymentStatus)
     - DeptID (duplicate of Department)
     - PositionID (duplicate of Position)
     - PerfScoreID (duplicate of PerformanceScore)
     - ManagerID (duplicate of Manager name)
     - From diverssity job fairs
     - 
### 8. Add Derived Columns

**Age** — calculated via Add Column > Custom Column:
```m
  = Number.RoundDown(Duration.Days(Date.From(DateTime.LocalNow()) - [DOB]) / 365.25)
````

**Tenure_Years** — calculated via Add Column > Custom Column:
```Excel

   = Number.RoundDown(Duration.Days((if [DateofTermination] = null then Date.From(DateTime.LocalNow()) else [DateofTermination]) - [DateofHire]) / 365.25)
```
**TerminationYear** — calculated via Add Column > Custom Column:

```` Excel
= If [DateofTermination] = null then "Still Employed" else Number.ToText(Date.Year([DateofTermination]))
````
**Salary_Range** — calculated via Add Column > Custom Column:
```Excel
= if [Salary] < 50000 then "Under $50k"
else if [Salary] < 75000 then "$50k-$75k"
else if [Salary] < 100000 then "$75k-$100k"
else if [Salary] < 150000 then "$100k-$150k"
else "$150k+"
````
### 9. Load to Excel
- Clicked Close & Load to bring the cleaned table into a new worksheet, used as the source for all PivotTables and the dashboard.
Final Column Count
- Started at 36 columns → removed 10 redundant ID columns → added 5 derived columns (TermReason_Category, Age, Tenure_Years, TerminationYear, Salary_Range) → 34 columns in the final cleaned dataset.
