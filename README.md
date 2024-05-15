# HR Analytics Project for Atliq Technologies

This project aims to analyze the attendance data of employees at Atliq Technologies for the last three months. The goal is to provide insights to the HR Generalist regarding employee attendance patterns, retention strategies, and reasons behind sick leave percentages. Additionally, the analysis differentiates between Work From Home (WFH) and Work From Office (WFO) percentages.

## Table of Contents

1. Project Description
2. Data Source
3. Requirements
4. Architecture Diagram
5. Technologies used
6. Methods
7. Results

## Project Description

The HR Analytics Project involved extracting, transforming, and loading attendance data from an Excel file into Power BI Desktop. The transformed data was then used to generate valuable insights using visualizations and dashboards.

## Data Source

The attendance data was provided in an Excel file format.
https://shorturl.at/sxDZ7
Access as an editor can be granted upon request.

## Requirements

To accomplish the project objectives, the following steps were taken:

1. **Understanding the Problem**: Define the scope of the analysis, focusing on attendance patterns, retention strategies, and sick leave percentages.
2. **Data Gathering and Transformation**: Collect the attendance data from the provided Excel file and perform ETL operations to clean and transform the data into a suitable format for analysis.
3. **Creating Metrics using DAX**: Implement Data Analysis Expressions (DAX) to create key metrics, such as attendance percentages, sick leave percentages, WFH percentages, and more.
4. **Dashboarding with Power BI Desktop**: Utilize Power BI Desktop to visualize the data and create interactive dashboards. Develop visualizations to provide insights into attendance trends, sick leave reasons, WFH vs. WFO percentages, and other relevant metrics.

## Architecture diagram


https://github.com/JonasGiven/HR-data-attendance-analysis-for-Atliq-technologies/assets/169194581/f0b99f8b-a25d-4c69-8fb4-3030e36119f3


## Technologies Used

The following technologies were used in this project:

- **MySQL**
- **Excel**
- **Power BI Desktop**

## Methods

A step-by-step approach on how I created visuals in Power BI from Excel and MySQL data:

**Step 1: Data Preparation in Excel**
The data in the Excel file needed to be cleaned before using it in Power BI. The initial goal was to have the date as a column with all the counts per day for Present (P), Sick Leave (SL), Total Working Days (TWD), and Work From Home (WFH).

Example: On June 1st, how many employees registered as Present (P)?

To achieve this, follow these steps:
1. Highlight the entire table and copy it.
2. Open a new worksheet in Excel, go to the first cell, right-click, and select "Paste Special" -> "Transpose."
3. Add columns for P, SL, TWD, and WFH at the end.
4. Use Excel functions to count P: `=COUNTIF(range, "P")`. This function counts the letter "P" for each day.
5. Repeat step 4 for SL, WFH, and use `=SUM(WFH + P)` for TWD.

Now, you have all the necessary columns to create DAX measures for SL%, WFH%, and P% in Power BI.

**Step 2: Data Transformation in MySQL**
When deleting unwanted columns (like employee names) in Excel, it affected the formulas for P, SL, WFH, and TWD, causing errors. To solve this, you used MySQL:

1. Create a schema for HR attendance in MySQL.
2. Upload the modified data with the relevant columns to the MySQL table.
3. Execute the following SQL code to retrieve the data:

```sql
SELECT date, P, SL, TWD, WFH
FROM attendance.attendance_tb;
```

Note: 'attendance' is the schema name, and 'attendance_tb' is the table name.

You repeated this process for each month separately and saved the resulting tables.

**Step 3: Data Loading and Transformation in Power BI**
1. Upload the saved tables from MySQL into Power BI.
2. Before loading the data, further transform it in the Power Query Editor:
   - Ensure each column corresponds to the relevant data type.
   - Create or add a column for SL% using the DAX measure: `SL% = [SL counts] / [Total working days]`.
   - Repeat the same for P% and WFH%.
3. Perform these steps for all three months.
4. Load the three datasets into Power BI.

**Step 4: Creating Visuals in Power BI**
1. Create visuals by dragging and dropping the relevant fields from the loaded datasets.
2. Use the Power Query Editor to combine data from all three months to create visuals for the overall period.
3. To create a bar chart with a line graph for each employee:
   - Use the Power Query Editor on the original (untransposed) Excel data.
   - Drop all columns except Employees, P, SL, PL, WFH, and TWD.
   - This data table will provide the total counts of P, SL, PL, WFH, and TWD for each employee per month.

By following these steps, you can transform the data from Excel and MySQL into visuals in Power BI.

## Results.

Here is the preview of the dashboard.


![IMG_0091](https://github.com/JonasGiven/HR-data-attendance-analysis-for-Atliq-technologies/assets/169194581/9e3faa56-1a34-498d-a556-03a763a995ef)


Use this link to access the dashboard in powerBI. You must copy this link and open a new tab on your browser, then paste it. https://shorturl.at/qrLUW
You might need to install powerBI desktop on your device. You can follow this link to download PowerBI - https://shorturl.at/acfQY

