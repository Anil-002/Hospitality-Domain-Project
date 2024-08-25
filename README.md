# Hospitality-Domain-Project
A data analysis project on hospitality domain using Power BI
## Project Title:
Provide Insights to the Revenue Team in the Hospitality Domain
## Project Overview:
This project aimed to conduct a comprehensive analysis of business performance for AtliQ Grands over the past 3 months, with the aim of identifying trends, and factors influencing revenue generation. By analyzing various aspects of Atliq Grands's operations, including revenue generation, occupancy trends, customer booking behavior, and service quality, the project sought to provide actionable insights to drive strategic decision-making on revenue management for the company.
## Business Problem:
AtliQ Grands, a leading hospitality company, owns multiple five-star hotels across India. They have been in the hospitality industry for the past 20 years. Due to strategic moves from other competitors and ineffective decision-making in management, AtliQ Grands are losing its market share and revenue in the luxury/business hotels category.
## Project Objective:
The primary objective of this data analysis project is to help AtliQ Grands regain its market share and revenue in the luxury/business hotels category by incorporating business and data intelligence into their revenue management strategies. This involves analyzing historical data and providing actionable insights to the revenue team.
## Project Scope:
- Gather historical data on relevant metrics.
- Analysis of historical data related to revenue, occupancy rates, booking patterns.
- Development of key performance metrics aligned with revenue management objectives.
- Creation of a user-friendly dashboard that visualizes important metrics and provides a comprehensive overview of the revenue management performance.
-	Generation of actionable insights and recommendations to the revenue team based on data analysis findings.
-	Documentation of the data analysis process, findings, and recommendations.
## Data Collection:
The dataset, sourced from codebasics.io, consists of five CSV files, each containing a separate table.
-	dim_date: Provides meta-information regarding dates, including month, week number, and day type (e.g., weekday or weekend).
-	dim_hotels: Contains essential metadata about hotel properties, such as property ID, property name, category (e.g., Luxury, Business), and city.
-	dim_rooms: Information about room types, including room ID and class. 
-	fact_aggregated_bookings: Aggregated booking data, including property ID, check-in date, room category, successful bookings, and capacity.
-	fact_bookings: Detailed booking data, including booking ID, property ID, booking date, check-in/out dates, number of guests, room category, booking platform, ratings given, booking status, revenue generated, and revenue realized.
## Data Preparation and Modeling:
All data was loaded into Power BI and extensively inspected to ensure quality and integrity. This inspection included checks for missing values, significant outliers, correct data types, and proper formatting. Subsequently, relationships between the tables were established for effective data modeling.
![Screenshot 2024-03-01 153457](https://github.com/arbayzid/Hospitality-Domain-Data-Analysis/assets/146184500/665d041e-afc3-488e-ab45-7ea11996e5c5)
## Data Analysis:
Some of the key measures created for in depth analysis has been listed below:  \
**Total Revenue:**
```
Revenue = SUM(fact_bookings[revenue_realized])
```
**Revenue Current Week:**
```
Revenue CW = 
VAR WeekNumber =
    IF (
        HASONEFILTER ( dim_date[wn] ),
        SELECTEDVALUE ( dim_date[wn] ),
        MAX ( dim_date[wn] )
    )
RETURN
    CALCULATE ( [Revenue], dim_date[wn] = WeekNumber )
```
**Revenue Previous Week:**
```
Revenue PW = 
VAR WeekNumber =
    IF (
        HASONEFILTER ( dim_date[wn] ),
        SELECTEDVALUE ( dim_date[wn] ),
        MAX ( dim_date[wn] )
    )
RETURN
    CALCULATE (
        [Revenue],
        FILTER ( ALL ( dim_date ), dim_date[wn] = WeekNumber - 1 )
    )
```
**Revenue Week-on-Week growth:**
```
Revenue WoW Growth = 
DIVIDE ( [Revenue CW] - [Revenue PW], [Revenue PW], 0 )
```
**Dynamic Color for Revenue Week-on-Week growth:**
```
Color Revenue Wow Growth = 
    IF([Revenue WoW Growth] > 0, "green",
        IF([Revenue WoW Growth] < 0, "red", "gray"))
```
**Occupancy Rate:**
```
Occupancy Rate = DIVIDE([Checked Out Bookings], [Total Capacity],0)
```
**Realisation Rate:**
```
Realisation Rate = DIVIDE([Checked Out Bookings], [Bookings],0)
```
**Revenue Per Available Room:**
```
RevPAR = DIVIDE([Revenue], [Total Capacity], 0)
```
**Average Daily Rate:**
```
ADR = DIVIDE([Revenue], [Bookings], 0)
```
## Dashboard Design and Development:
Design and mock-up of a user-friendly dashboard have been developed using Figma to incorporate relevant metrics and visualizations, providing a comprehensive overview of revenue management performance.
## ScreenShots:
![HOME](https://github.com/user-attachments/assets/b1d8c023-d73a-4d51-9fd9-51d8ad799c02)

## Conclusion:
By leveraging data analysis and business intelligence, AtliQ Grands aims to enhance its revenue management capabilities, drive revenue growth, and regain market share in the competitive hospitality industry. This project will empower the revenue team with actionable insights and strategic recommendations, enabling informed decision-making and sustainable business success.
