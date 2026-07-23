# Power Query ETL & Data Hygiene Pipeline

## Project Overview
An end-to-end data cleaning and ETL project built using Power Query to transform a messy, raw workforce dataset into an analytics-ready structure. This project focuses on hands-on data profiling, spotting inconsistencies, handling missing values strategically, and ensuring robust type safety for automated reporting.

## Key Engineering Decisions & Data Hygiene
* **Strategic Null Preservation:** Discovered that roughly 21% of employee ages and 2% of salary entries were missing. Instead of deleting valuable rows and losing primary key data (`Employee ID`), I deliberately preserved them as true database `null` values to keep row counts intact and protect aggregate calculations.
* **Error Handling & Normalization:** Handled messy text entries and standard string anomalies (like `"N/A"` in salaries and formatting hyphens in phone numbers) by normalizing them into safe nulls prior to executing data type conversions, ensuring downstream refresh stability.
* **Column Restructuring & Splitting:** Took combined string attributes (`Department_Region`) and split them by delimiter into distinct, clean analytical dimensions (`Department` and `State`), followed by intentional header renaming and strict data type enforcement.
* **Readable Formatting:** Maintained clean, user-friendly column casing and layout throughout the transformation steps for optimal readability.

## Visualizing the Data Quality Process

### 1. Diagnosing Missing Data (Column Quality Tool)
Here is a snapshot of the raw data profiling phase, using Power Query's Column Quality tool to identify missing values and structural anomalies before transformation. You can clearly see the ~21% empty/null values in the column here, which confirmed the need for our strategic null preservation:

![Column Quality Profiling](https://raw.githubusercontent.com/AdamLumbley/power-query-etl-cleaning/main/HR-column-quality-profiling.png)

### 2. Transformation Pipeline (Applied Steps Pane)
Here is the sequential view of the Power Query Applied Steps pane, showcasing the fully audited transformation workflow from source extraction through normalization, splitting, and type enforcement:

![Applied Steps Pipeline](https://raw.githubusercontent.com/AdamLumbley/power-query-etl-cleaning/main/hr-dataset-applied-steps.png)

## Repository Structure
* `power_query_script.txt` - The complete, end-to-end M-code script executing the ETL transformations in Power Query.
