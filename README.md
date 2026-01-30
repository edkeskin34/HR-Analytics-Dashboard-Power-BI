# HR Analytics Dashboard - Power BI

## Project Objective

In this project, I designed and built an end-to-end HR Analytics dashboard in Power BI to support data-driven decision-making within an HR department.

My objective was to convert raw HR data into clear, actionable insights by integrating demographic analysis, performance tracking, time-based trends, and employee attrition drivers into a single, well-structured analytical model.

---

## Data Modeling Approach

I designed the data model using a **star schema** to ensure clarity, scalability, and strong analytical performance.  
I deliberately separated fact and dimension tables to enable flexible slicing, accurate aggregations, and consistent filtering behavior.

### Key Tables in the Model

- **FactPerformanceRating**  
  I used this table to store employee performance reviews, satisfaction metrics, ratings, and review dates.

- **DimEmployee**  
  I designed this dimension to capture employee demographic and organizational attributes such as HireDate, Department, and JobRole.

- **DimDate**  
  I created a custom calendar table to support all time-based analyses across the report.

- **DimSatisfiedLevel / DimRatingLevel**  
  I used these tables to translate numeric scores into meaningful categorical levels for interpretation.

---

## DimDate (Calendar Table)

To ensure consistent and reliable time-based analysis, I created a custom **DimDate** table using DAX.

My goals were to:

- Analyze multiple date fields (HireDate, ReviewDate) on a single, unified time axis  
- Enable year, quarter, month, week, and fiscal-year breakdowns  
- Support accurate time-intelligence calculations and trend analysis  

I built the DimDate table dynamically based on the minimum and maximum employee hire dates, allowing the model to scale seamlessly as new data is added.

---

## _Measures Table (Calculation Layer)

I centralized all DAX calculations in a dedicated **_Measures** table to create a clear calculation layer.

This approach allowed me to:

- Improve overall model readability  
- Maintain a clean separation between data structure and business logic  
- Reuse measures consistently across multiple report pages and visuals  

---

## DAX Usage

DAX played a central role throughout this project.  
I deliberately applied advanced DAX functions to control filter context, activate relationships, and ensure accurate calculations:

- **CALCULATE()** – to modify filter context dynamically  
- **USERELATIONSHIP()** – to activate inactive date relationships when required  
- **DIVIDE()** – to calculate rates safely and avoid division errors  
- **SELECTEDVALUE()** – to enable single-employee drill-down analysis  
- **FORMAT()** – to improve the readability of dates and percentage values

  ---
This DAX-driven approach allowed me to perform flexible analysis from a single data model while preserving both accuracy and performance.

---

## Report Pages and Analytical Goals

### Overview

I designed the Overview page to provide executive-level insight at a glance.

On this page, I summarized:

- Total, active, and inactive employee counts  
- Overall attrition rate  
- Hiring and attrition trends over time  
- Employee distribution by department and job role  

My goal was to present a high-level workforce snapshot in a single, intuitive view.

![Overview Page](images/overview_page.png)

---

### Demographics

I built the Demographics page to analyze workforce composition and diversity.

This page includes:

- Age distribution analysis  
- Age and gender breakdowns  
- Marital status composition  
- Ethnicity combined with average salary analysis  

The purpose of this page was to support Diversity & Inclusion (D&I) insights and long-term workforce planning.

---

### Performance Tracker

I designed the Performance Tracker page to monitor individual employee performance over time.

Key features include:

- An employee selection slicer  
- Hire date, last review date, and next review date indicators  
- Time-based trends for job satisfaction, environment satisfaction, and work-life balance  
- A comparison between self-ratings and manager ratings  

My objective was to identify alignment or gaps between employee self-perception and managerial evaluation.

---

### Attrition

I built the Attrition page to analyze why employees leave and under which conditions.

On this page, I analyzed attrition by:

- Department and job role  
- Business travel frequency  
- Overtime requirements  
- Years at the company  
- Hire-date-based time trends  

The goal of this analysis was to generate actionable insights that can inform effective employee retention strategies.
