# Airline-Data-Analysis-SQL-Project

This project is focused on analyzing airline data to answer specific business questions using SQL. By querying the database, I extract insights about airline performance, geographic trends, and aircraft types.

## Objective

The main goal of this project is to solve real-world airline business questions using SQL queries. This includes identifying top-performing airlines, analyzing aircraft and region statistics, and comparing performance between major manufacturers like Boeing and Airbus.

 ## Questions Solved
Below are the 5 questions addressed in this project, with a step-by-step explanation:

Qustion 1. Which airlines have the highest total landed weight for all regions combined?
```sql
SELECT TOP 5
    Published_Airline, 
    SUM(Total_Landed_Weight) AS Total_Landed_Weight
FROM 
    Airline
GROUP BY 
    Published_Airline
ORDER BY 
    Total_Landed_Weight DESC;
```

Qustion 2. What is the average number of landings by aircraft body type across all regions?
```sql
SELECT 
    Aircraft_Body_Type, 
    AVG(Landing_Count) AS Avg_Landing_Count
FROM 
    Airline
GROUP BY 
    Aircraft_Body_Type;
```


Qustion 3. Identify the top 5 geographic regions based on total landed weight?
```sql
SELECT 
    GEO_Region, 
    SUM(Total_Landed_Weight) AS Total_Landed_Weight
FROM 
    Airline
GROUP BY 
    GEO_Region
ORDER BY 
    Total_Landed_Weight DESC
```

Qustion 4. Compare the total landed weight and landing counts for Boeing vs. Airbus across regions?
```sql
SELECT 
    Aircraft_Manufacturer, 
    GEO_Region, 
    SUM(Total_Landed_Weight) AS Total_Landed_Weight, 
    SUM(Landing_Count) AS Total_Landing_Count
FROM 
    Airline
WHERE 
    Aircraft_Manufacturer IN ('Boeing', 'Airbus')
GROUP BY 
    Aircraft_Manufacturer, 
    GEO_Region
ORDER BY 
    Total_Landed_Weight DESC;
```

Qustion 5. Which aircraft model contributes the most to total landed weight in the "Asia" region?
```sql
SELECT TOP 1 
    Aircraft_Model, 
    SUM(Total_Landed_Weight) AS Total_Landed_Weight
FROM 
    Airline
WHERE 
    GEO_Region = 'Asia'
GROUP BY 
    Aircraft_Model
ORDER BY 
    Total_Landed_Weight DESC
```

## How to Use
You can download the SQL queries file from this repository.
Create Database called Arilines_data.
Populate the Airline table with relevant data (e.g., airline names, regions, aircraft types, landed weights, etc.).
Execute the queries on your SQL database to answer the business questions.

## Tools Used
SQL: For querying and analysis. <br>
Relational Database: To store and manage airline data.

## Conclusion
This project demonstrates the use of SQL for solving key analytical questions in the aviation industry. The insights obtained can help airlines optimize their operations, understand regional trends, and evaluate aircraft performance.
