# Churn-DataSet-Analysis-Dashboard

📊 Customer Churn Data Analysis & Dashboard

An end-to-end Customer Churn Data Analysis project built to demonstrate practical data analyst skills using Python, Pandas, NumPy, SQL, MySQL, Excel, and Power BI.

The project starts with an unclean customer dataset, performs data cleaning and validation in Python, engineers analytical features, loads the cleaned data into MySQL for SQL analysis, and finally presents customer churn and revenue insights through an interactive Power BI dashboard.

📌 Project Overview

Objective:
Analyze customer behavior, revenue, subscription patterns, and churn to identify useful business insights that can support customer-retention analysis.

End-to-end workflow:

Raw Excel Dataset → Python Data Cleaning → Feature Engineering → Clean CSV → MySQL → SQL Analysis → Power BI Dashboard

🛠️ Tools & Technologies

Python — Pandas, NumPy

Microsoft Excel — source dataset

MySQL / MySQL Workbench — data storage and SQL analysis

SQL — aggregations, filtering, grouping, churn analysis

Power BI Desktop — interactive dashboard and visualization

Jupyter Notebook — data cleaning and preprocessing

📂 Project Structure

Customer-Churn-Data-Analysis/
│
├── Churn dataset cleaning.ipynb     # Data cleaning & preprocessing
├── Churn_Unclean_Project.xlsx       # Original unclean dataset
├── Clean_Churn_Data.csv              # Processed dataset
├── sql.sql                           # SQL analysis queries
├── PowerBI Dekstop.pbix              # Power BI dashboard
├── dashboard.png                     # Dashboard screenshot
└── README.md                         # Project documentation

🧹 Data Cleaning & Preprocessing

The raw Excel dataset contains 542 records and 18 columns before preprocessing.

The Python notebook performs the following tasks:

Loaded the Excel dataset using Pandas.

Inspected the dataset using head(), info(), describe(), and shape.

Checked missing values across columns.

Detected and removed 7 duplicate records.

Replaced dirty placeholder values such as N/A, NULL, and blank strings with NaN.

Removed extra spaces from text fields.

Standardized categorical values using proper case formatting.

Standardized the Churn column to Yes / No.

Converted numeric columns to numeric data types.

Removed invalid age values outside the 18–100 range.

Removed negative values from Monthly_Charges and Total_Charges.

Converted Last_Interaction_Date to a date format.

Filled selected missing values using logical defaults or statistical measures.

Created additional analytical features.

Exported the processed data to CSV.

Loaded the final dataset into MySQL for SQL analysis.

🔧 Feature Engineering

The project creates additional fields to support analysis:

Customer Value

df["Customer_Value"] = df["Monthly_Charges"] * df["Tenure_Months"]

Estimates customer value using monthly charges and customer tenure.

Monthly Revenue

df["Monthly_Revenue"] = df["Monthly_Charges"]

Creates a revenue field for reporting and dashboard analysis.

Tenure Group

Customers are grouped into:

0-12

13-24

25-48

49-72

Senior Flag

df["Senior_Flag"] = np.where(df["Age"] >= 60, "Senior", "Adult")

Creates an age-based customer segment.

Churn Flag

df["Churn_Flag"] = df["Churn"].map({
    "Yes": 1,
    "No": 0
})

Converts churn status into a numeric flag for analysis.

🗄️ MySQL Analysis

The cleaned dataset is loaded into a MySQL table named:

customer_churn

The SQL analysis includes queries for:

Total customer count

Total churned customers

Overall churn rate

Average monthly charges

Average customer tenure

Customers by contract type

Customers by internet service

Churn by state

Customers by payment method

Customers by subscription type

Revenue by state

Average monthly charges by contract type

Senior-citizen churn

Top 10 high-value customers

Customers without technical support

Example: Churn Rate

SELECT
ROUND(
    SUM(CASE WHEN Churn='Yes' THEN 1 ELSE 0 END) * 100 / COUNT(*),
    2
) AS Churn_Rate
FROM customer_churn;

This calculates the percentage of customers whose churn status is Yes.


## 📊 Power BI Dashboard

The interactive Power BI dashboard provides insights into customer churn, revenue, customer retention, monthly charges, contract types, subscription types, internet services, and state-wise revenue.

### Dashboard Preview

![Churn DataSet Analysis Dashboard](dashboard.png)

📈 Power BI Dashboard

The Power BI dashboard provides an interactive view of customer and churn performance.

Dashboard includes

Payment Method slicer

Total Revenue

Total Customers

Retained Customers

Churn Rate

Churn Customers

Average Monthly Charges

Average Tenure

Churn by Senior Citizen

Churn by Internet Service

Total Revenue by State

Churn by Contract Type

Monthly Charges vs. Churn Flag

Churn by Subscription Type

Dashboard Screenshot



📊 Final Dataset

After preprocessing and filtering, the exported dataset contains 492 customer records and 23 columns, including engineered fields such as:

Customer_Value
Monthly_Revenue
Tenure_Group
Senior_Flag
Churn_Flag

The cleaned dataset is available in:

Clean_Churn_Data.csv

🔍 Sample Analytical Findings

Based on the processed dataset:

492 customer records were exported for analysis.

374 records have Churn = No.

116 records have Churn = Yes.

2 records still have missing churn values in the exported dataset.

Total Total_Charges across the exported records are approximately 24.78M.

The average monthly charge is approximately 1,359.22.

The average tenure is approximately 36.06 months.

These figures describe the project dataset used in this repository and are not intended to represent a real-world customer population.

🎯 Skills Demonstrated

This project demonstrates practical experience in:

Data cleaning and preprocessing

Exploratory data analysis

Missing-value handling

Duplicate detection and removal

Data validation

Feature engineering

Pandas and NumPy

SQL querying

MySQL database handling

Power BI dashboard development

KPI creation

Data visualization

Business-oriented customer churn analysis

🚀 How to Run the Project

1. Clone the repository

git clone <your-repository-url>
cd Customer-Churn-Data-Analysis

2. Install Python dependencies

pip install pandas numpy openpyxl sqlalchemy pymysql

3. Run the notebook

Open:

Churn dataset cleaning.ipynb

Run the notebook from top to bottom to reproduce the cleaning and feature-engineering workflow.

4. Load data into MySQL

Create a MySQL database and update the notebook's SQLAlchemy connection with your own local MySQL credentials.

Do not commit passwords or private credentials to GitHub.

5. Run SQL analysis

Open:

sql.sql

in MySQL Workbench and execute the queries against the customer_churn table.

6. Open the Power BI dashboard

Open:

PowerBI Dekstop.pbix

and refresh the data source if necessary.

📌 Notes

The original Excel file is intentionally included to show the complete cleaning workflow.

The Power BI file may require local data-source path updates after cloning.

The notebook contains the reproducible preprocessing steps used to generate the CSV and MySQL table.

The screenshot in dashboard.png shows the dashboard created for the project.

👤 Author

Shivaji Gorakh Zine
Computer Engineering Student | Data Analytics | SQL | Python | Power BI
