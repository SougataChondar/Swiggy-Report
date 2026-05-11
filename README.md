# 🍕 Swiggy Sales Case Study

---

## 📝 Introduction
This project is a complete Swiggy Sales Case Study built using SQL Server for data cleaning, data modeling, transformation, and business analysis.

The goal of this project is to analyze Swiggy food delivery data to extract meaningful business insights related to:

- Sales performance
- Customer ratings
- Restaurant trends
- Food category analysis
- Revenue insights
- Location-based performance

The project demonstrates practical skills in:

- SQL querying
- Data cleaning & validation
- Star schema data modeling
- Fact & dimension table creation
- KPI analysis
- Business intelligence reporting

## 🛠️ Tools & Technologies Used
- **SSMS (SQL Server Management Studio)** : Database Management, Data Cleaning & Analysis, Query Execution.

## 📂 Dataset Description
The dataset contains Swiggy food ordering information including:

- State
- City
- Order Date
- Restaurant Name
- Food Category
- Dish Name
- Price
- Ratings
- Rating Count
- Delivery Location

## 📊 Project Overflow
### 1️⃣ Data Validation & Cleaning
The first stage of the project focused on ensuring the quality and consistency of the dataset.

✔ **Null Value Check**

Performed null checks on important columns:

- State
- City
- Order Date
- Restaurant Name
- Location
- Category
- Dish Name
- Price
- Rating
- Rating Count

✔ **Blank Value Detection**

Identified records containing empty strings or missing text values.

✔ **Duplicate Detection**

Used:
```sql
ROW_NUMBER()
```
To identify duplicate rows based on multiple business columns.

✔ **Duplicate Removal**

Removed duplicate records using:
```sql
CTE + ROW_NUMBER()
```
This improved data consistency and prevented incorrect KPI calculations.

## 🏗️ Data Modeling
A Star Schema data model was created for optimized analytics and reporting.

### 📌 Dimension Tables

🗓️ **dim_date**

Contains:

- Full Date
- Year
- Month
- Month Name
- Quarter
- Day
- Week

📍 **dim_location**

Contains:

- State
- City
- Delivery Location

🍽️ **dim_restaurant**

Contains restaurant names.

🍕 **dim_category**

Contains food categories.

🍜 **dim_dish**

Contains dish names.

### 📌 Fact Table

📦 **fact_swiggy_orders**

Stores transactional order data including:

- Price
- Rating
- Rating Count
- Date ID
- Restaurant ID
- Location ID
- Category ID
- Dish ID

The fact table is connected with all dimension tables using foreign keys.

## 🔗 Star Schema Architecture
```text
                 dim_date
                     |
                     |
dim_location --- fact_swiggy_orders --- dim_restaurant
                     |
                     |
               dim_category
                     |
                     |
                  dim_dish
```
## 📥 Data Loading Process

Data was inserted into dimension tables using:
```sql
SELECT DISTINCT
```
This This avoided duplicate dimensional records.

The fact table was populated using:
```sql
INNER JOIN
```
between staging data and all dimension tables.

## 📈 Key Performance Indicators (KPIs)

The following business KPIs were created:
### ✅ Total Orders

Measures total number of orders processed.
```sql
SELECT COUNT(*)
```
### ✅ Total Revenue

Calculated total revenue generated in INR Millions.
```sql
SUM(price_INR)
```
### ✅ Average Dish Price

Analyzed average selling price of dishes.
```sql
AVG(price_INR)
```
### ✅ Average Rating

Calculated overall customer satisfaction.
```sql
AVG(Rating)
```
## 📌 Business Insights Generated

This project can help businesses answer questions like:

- Which cities generate the highest revenue?
- Which restaurants receive the best ratings?
- Which food categories are most popular?
- What is the average order value?
- Which dishes perform best?
- Which locations contribute most to sales?
- What are the monthly sales trends?

---

## 🚀 How to Run the Project
### Step 1: Import Dataset
Import the Swiggy dataset into SQL Server.

### Step 2: Run Cleaning Queries

Execute:

- Null checks
- Duplicate detection
- Duplicate removal

### Step 3: Create Tables

Run all:

- Dimension table creation queries
- Fact table creation queries

### Step 4: Insert Data

Populate dimension and fact tables.

### Step 5: Run KPI Queries

Execute analytical queries to generate insights.

## 📁 Project Structure
```text
📦 Swiggy-Sales-Case-Study
 ┣ 📄 SQLQuery1.sql
 ┣ 📄 README.md
 ┗ 📄 Dataset.csv
```
## 💡 Future Improvements

Possible enhancements for this project:

- Build Power BI Dashboard
- Add advanced SQL analytics
- Implement stored procedures
- Add trend forecasting
- Create interactive visualizations
- Include customer segmentation analysis

---

## 📌 Conclusion

This Swiggy Sales Case Study demonstrates end-to-end SQL analytics workflow starting from raw data cleaning to dimensional modeling and KPI generation.

The project reflects practical industry-level understanding of:

- Data Warehousing
- SQL Analytics
- Business Intelligence
- Reporting & KPI Tracking

---
## ❤️ Contributing
Contributions are welcome! Fork the repository, create a new branch, and submit your pull request with improvements or new features.

---

✨ Let’s use data to make informed decisions and create safer communities! ✨
