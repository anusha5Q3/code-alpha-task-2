TASK 2: Human Resources Analytics – Complete Solution
✓Objective
Create an interactive Power BI dashboard to analyze and optimize HR processes and workforce management, focusing on recruitment, employee turnover, satisfaction, performance, and hiring forecasts.
1. Data Model (Recommended Tables)
✓Employee Table
Column Name
Description
EmployeeID
Unique employee ID
Gender
Male / Female
Department
HR, IT, Sales, Finance
JobRole
Job title
HireDate
Employee joining date
ExitDate
Employee leaving date (blank if active)
PerformanceRating
1–5 scale
SatisfactionScore
1–5 scale
Salary
Monthly salary
2 Recruitment Table
Column Name
Description
CandidateID
Unique candidate ID
JobRole
Role applied
ApplicationDate
Application date
HireStatus
Hired / Rejected
TimeToHire
Days taken to hire
 Relationship:-
Employee[JobRole] → Recruitment[JobRole]
2.Key DAX Measures (As per Rules)
  Total Employees
Copy code
DAX
Total Employees =
COUNT(Employee[EmployeeID])
  Active Employees
Copy code
DAX
Active Employees =
CALCULATE(
    COUNT(Employee[EmployeeID]),
    ISBLANK(Employee[ExitDate])
)
  Employees Left
Copy code
DAX
Employees Left =
CALCULATE(
    COUNT(Employee[EmployeeID]),
    NOT(ISBLANK(Employee[ExitDate]))
)
 Employee Turnover Rate (%)
Copy code
DAX
Turnover Rate % =
DIVIDE(
    [Employees Left],
    [Total Employees],
    0
) * 100
  Average Employee Satisfaction
Copy code
DAX
Avg Satisfaction Score =
AVERAGE(Employee[SatisfactionScore]).
   Average Performance Rating
Copy code
DAX
Avg Performance Rating =
AVERAGE(Employee[PerformanceRating])
   Total Hires
Copy code
DAX
Total Hires =
CALCULATE(
    COUNT(Recruitment[CandidateID]),
    Recruitment[HireStatus] = "Hired"
)
  Average Time to Hire (Days)
Copy code
DAX
Avg Time to Hire =
AVERAGE(Recruitment[TimeToHire])
3 Predictive Analytics – Hiring Forecast
  Hiring Trend (Monthly)
Copy code
DAX
Monthly Hires =
CALCULATE(
    [Total Hires],
    DATESMTD(Employee[HireDate])
)
  Use Power BI Forecast option on a line chart:
X-Axis: Hire Date (Month)
Values: Monthly Hires
Enable Analytics → Forecast
Forecast length: 6–12 months
  This predicts future hiring needs based on historical data.
4Dashboard Pages & Visuals
   Page 1: HR Overview
KPI Cards:
Total Employees
Active Employees
Turnover Rate %
Donut Chart:
Employees by Department
Bar Chart:
Employees by Job Role
  Page 2: Recruitment Analytics
KPI Cards:
Total Hires
Avg Time to Hire
Line Chart:
Hiring Trend with Forecast
Bar Chart:
Hires by Job Role
   Page 3: Employee Performance & Satisfaction
Gauge:
Avg Satisfaction Score
Column Chart:
Performance Rating by Department
Scatter Chart:
Satisfaction vs Performance
5 Business Insights Delivered
   Identify departments with high turnover
  
  Monitor employee satisfaction & performance gaps
  Analyze recruitment efficiency
  Predict future hiring needs
  Enable data-driven HR decisions
6.  Final Deliverable (As Required)
    Interactive Power BI Report
    Dynamic filters (Department, Job Role, Gender)
# code-alpha-task-2
