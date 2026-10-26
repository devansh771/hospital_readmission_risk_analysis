
# <p align="center">Hospital Readmission Risk Analysis</p>
# <p align="center">![Hospital Dashboard](hospital-dashboard.jpg)</p>

## Business Problem
Hospitals face challenges in identifying patients who may be readmitted within 30 days of discharge. This project analyzes historical data from 130 U.S. hospitals to explore readmission patterns across diagnosis categories, hospital length of stay, A1C results, prior utilization, medication use, and discharge destinations.

The goal is to identify patterns that can help healthcare teams prioritize follow-up care and improve discharge planning. This is a descriptive analysis project, not a validated predictive model.

## Dataset & Tools
- **Dataset:** Diabetes 130-US Hospitals for Years 1999–2008
- **Source:** UCI Machine Learning Repository
- **Coverage:** Approximately 100,000 hospital encounters across 130 U.S. hospitals
- **Tools:** MySQL Workbench, Power BI
- **SQL Techniques:** CTEs, window functions (`RANK`, `NTILE`), `CASE` statements, correlated subqueries, aggregations, and multi-table joins
- **Visualization:** Power BI KPI cards, bar charts, a line chart, and interactive slicers

## Project Approach

### 1. Data Cleaning
- Replaced placeholder missing values with `NULL` where applicable.
- Evaluated missingness in key columns.
- Created a cleaned analysis table by retaining one encounter per patient.
- Excluded selected discharge disposition categories associated with hospice or deceased patients, according to the project's cleaning logic.
- Joined reference mapping tables to convert coded values into readable labels.

**Methodological note:** Keeping only one encounter per patient may affect readmission analysis because subsequent encounters can be relevant to the outcome. Readmission-rate calculations should therefore be interpreted in the context of the selected cohort.

### 2. Exploratory SQL Analysis
Used SQL to investigate:
- Overall readmission patterns
- Readmission rates by diagnosis category
- Readmission patterns by hospital length of stay
- Readmission rates by A1C result
- Readmission rates by discharge destination
- Relationships between prior inpatient utilization, medication use, and readmission

### 3. Advanced SQL Analysis
- Used CTEs to structure intermediate analysis datasets.
- Applied `RANK()` and `NTILE()` to rank and segment records.
- Used `CASE` statements to categorize diagnosis codes and create business-readable groups.
- Applied correlated subqueries and `HAVING` conditions to identify diagnosis categories with above-average readmission rates.
- Joined mapping tables to make coded fields interpretable.

## Power BI Dashboard

The Power BI dashboard brings the analysis together in an interactive report, allowing users to explore readmission patterns across selected patient and hospital characteristics.

### KPI Cards
- **Eligible Encounters or Patients:** Displays the record count from the selected analysis table.
- **30-Day Readmission Rate:** Displays the percentage of records marked as readmitted within 30 days.
- **Average Length of Stay:** Shows the average number of days spent in the hospital.
- **Average Medications per Encounter:** Shows the average number of medications recorded per encounter.

### Dashboard Visuals

**1. Readmission Rate by Length of Hospital Stay**
- A line chart comparing readmission rates across hospital-stay durations.
- Helps identify lengths of stay associated with higher observed readmission rates.

**2. Readmission Rate by A1C Result**
- A bar chart comparing readmission rates across A1C result categories, including `None`, `Norm`, `>7`, and `>8`.
- Helps explore differences in observed readmission rates across recorded A1C result groups.
- `None` represents missing or unrecorded A1C result information in the analysis.

**3. Readmission Rate by Diagnosis Categories**
- A bar chart comparing readmission rates across diagnosis categories.
- Highlights categories with higher observed readmission rates in the selected analysis cohort.

**4. Readmission Rate by Discharge Destination**
- A bar chart comparing readmission rates across selected discharge destinations.
- Helps identify destinations with higher observed rates, while recognizing that sample sizes and patient characteristics may differ across destinations.

### Interactive Slicers
The dashboard includes slicers for:
- Gender
- Age Group
- Admission Type
- Discharge Destination
- Change in Medication
- Readmission status

These slicers are intended to support interactive exploration of readmission patterns. Their behavior depends on the Power BI data model, relationships, visual interactions, and measure definitions.

## Key Findings
Based on the SQL analysis and dashboard outputs:

1. **Diagnosis categories:** Injury, circulatory conditions, and diabetes appeared among the categories with above-average readmission rates in the SQL analysis.
2. **Prior inpatient utilization:** The analysis identified prior inpatient utilization as an important factor associated with observed readmission patterns.
3. **Discharge destination:** Readmission rates varied across discharge destinations, indicating differences in the observed outcomes of patients discharged to different care settings.
4. **A1C results and medication changes:** The project explored readmission patterns across A1C result categories and medication-change status, during the stay both align with the original clinical research question this dataset was collected to investigate.
## Recommendations
- Explore enhanced follow-up planning for patient groups with higher observed readmission rates.
- Review discharge planning and care coordination for patients discharged to facilities with higher observed rates.
- Investigate prior inpatient utilization as a potential indicator for prioritizing follow-up assessment.
- Interpret A1C and medication-related patterns alongside missing-data limitations and other patient characteristics.

## Conclusion
This project demonstrates the use of SQL for healthcare data preparation and analysis, combined with Power BI for KPI reporting and interactive visualization. It explores how readmission patterns vary across diagnosis categories, length of stay, A1C results, prior utilization, medication use, and discharge destination.

The project emphasizes data quality, transparent KPI definitions, and careful interpretation of healthcare metrics to support evidence-informed operational analysis.
