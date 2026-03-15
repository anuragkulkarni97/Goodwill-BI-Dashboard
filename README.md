Goodwill Industries - Power BI Business Intelligence Dashboard

A comprehensive business intelligence project building an end-to-end Power BI dashboard for Goodwill Industries - Palm Beaches, Treasure Coast and Manasota. 

This repository covers the complete BI pipeline from synthetic data generation and data modelling through custom DAX measure development, Power Query transformations, and a six-page interactive dashboard, including a Python-powered OLS revenue forecast for FY2025.


The dashboard is built on a synthetic dataset modelled on real Goodwill operational data across 12 store locations, 8 product categories, and 5 workforce development programs spanning FY2023 through FY2024, submitted as a BI Analyst work sample in February 2025.

Key Features:


Star Schema Data Model: 

Designed the entire data model using a star schema pattern with two fact tables, FactSales and FactPrograms, and four dimension tables covering dates, stores, product categories, and workforce programs. 

All relationships are one-to-many from dimension to fact with single cross-filter direction to avoid ambiguity and maximise query performance.


Custom DAX Measures: 

Built eight custom DAX measures organized in a dedicated measures table, covering total revenue, revenue year-over-year growth using SAMEPERIODLASTYEAR time intelligence, gross margin percentage, a Goodwill-specific revenue-per-donated-pound efficiency KPI, rolling three-month revenue for noise smoothing, job placement rate, a Python-derived OLS forecast for FY2025, and a YTD revenue vs target gauge.


Python OLS Forecasting: 

Derived OLS regression coefficients, slope 67.35, intercept 19,005, R² approximately 0.87, by running a linear regression on 24 months of monthly revenue data in Python using NumPy polyfit. These coefficients are embedded directly into the DAX Forecast measure, bridging Python analysis with live Power BI reporting.


Power Query Transformations: 

Applied a full set of M transformations including null imputation for donation weights using store monthly averages, region name standardisation for join accuracy, whitespace trimming, data type casting, and a conditional performance tier column based on revenue quartile. The date table was auto-generated via CALENDAR spanning FY2023 through FY2025 and marked as the official date table for time intelligence.


Six-Page Interactive Dashboard: 

Built six dashboard pages covering an executive overview with KPI cards and year-over-year trend charts, a retail and donations deep-dive with category performance and correlation analysis, a store performance leaderboard with gross margin benchmarking, a mission programs impact summary with placement rates and community wages, a forecast and trend page with a 36-month chart and confidence interval bands, and a DAX reference page documenting every measure and calculated column directly inside the dashboard.


DAX Reference Page: 

Included an in-dashboard documentation page showing all measure formulas, calculated column definitions, and data model structure, ensuring any self-service user can understand the logic behind every metric without opening an external document.

Key Results - FY2024:

KPI   ,   FY2024  ,  vsFY2023

Total Revenue  ,  $293,486  , +4.7%

Donations Received   ,   261,586lbs   ,  +5.5%

Gross Margin    ,    77.1%    ,   +0.1pp

Job Placements   ,   6,747    ,   +5.2%

Avg Ticket Size   ,  $9.72   ,    +1.8%

FY2025 Forecast   ,   $299,400  ,  +2.0% projected

Tech Stack:


Power BI Desktop: For data modelling, DAX development, Power Query transformations, and dashboard design.

DAX: For eight custom measures and four calculated columns covering time intelligence, efficiency KPIs, and OLS forecasting.

Power Query (M): For data cleaning, date table generation, and column transformations.



How to Open:

Download Goodwill_BI_Dashboard_Anurag.pbix from this repository.

Open it with Power BI Desktop, which is available as a free download from Microsoft.

All data is embedded inside the file, no external database connections are required.

For a quick preview without installing Power BI, open Goodwill_BI_Dashboard.html in any web browser.

The full technical documentation covering the data model, all DAX measures, and the forecasting methodology is available in Goodwill_BI_Documentation.docx.


Future Work: 

This project provides a strong foundation for production BI reporting at Goodwill. 


Future improvements could include:

Live Data Connection: Replacing the embedded synthetic dataset with a direct connection to Goodwill's POS and donor management systems, enabling the dashboard to refresh automatically with real transaction-level data.

Automated Forecast Refresh: Moving the OLS regression from a static coefficient to a Python dataflow or parameterised M query that reruns the regression on each refresh, keeping the forecast coefficients current as new months of data arrive.

Anomaly Detection: Adding a DAX measure that flags stores or categories where the current month's revenue deviates more than two standard deviations from the rolling average, surfacing operational issues before they appear in quarterly reviews.

Donor Segmentation: Extending the data model with a donor dimension and building an RFM (Recency, Frequency, Monetary) segmentation model in Python, feeding donor tier assignments back into Power BI to analyse how donation behaviour drives revenue by store.

About:

Built by Anurag Kulkarni.

Connect on LinkedIn: https://www.linkedin.com/in/anurag-kulkarni97/

GitHub: AnalyticalAnurag97
