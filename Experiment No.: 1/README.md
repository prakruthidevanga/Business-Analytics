Retail Analytics — MySQL + Kaggle + Power BI Dashboard

A Business Analytics project that combines a relational MySQL database with a Kaggle flat file (CSV) inside a single, interactive Power BI report — giving a centralized view of sales, customer, and product performance for a retail business.

📌 Problem Statement

Transaction-level sales data (Customers, Products, Orders) is maintained in a MySQL database, while an additional reference dataset is available as a flat file (CSV) from Kaggle. This project builds the MySQL database, connects it to Power BI, imports the Kaggle file directly, models the combined data, and produces an interactive, insight-rich dashboard.

🛠️ Tech Stack
MySQL (Server + Workbench) — relational source database
Kaggle "Sample Superstore" dataset (CSV) — flat-file source
Power BI Desktop — data import, modeling, DAX, and dashboarding
Power Query — data cleaning and transformation
DAX — calculated measures

🚀 Setup & Steps
1. Set Up the MySQL Database- It creates the retail_analytics database with three related tables — Customers, Products, and Orders (fact table) — and inserts sample records. Verify with:

SELECT * FROM Customers;
SELECT * FROM Products;
SELECT * FROM Orders;

2. Get the Kaggle Flat File

Download the Sample Superstore dataset: 👉 https://www.kaggle.com/datasets/vivek468/superstore-dataset-final (search "superstore dataset" on Kaggle if the link changes; any similar retail CSV works) Save it as data/Superstore.csv.

3. Connect MySQL to Power BI
Install the MySQL Connector/NET (or MySQL ODBC 8.0 driver).
Power BI Desktop → Home → Get Data → More → MySQL database → Connect.
Server: localhost:3306, Database: retail_analytics.
Choose Import mode, enter credentials, select Customers, Products, Orders → Load.

5. Import the Kaggle CSV
Power BI Desktop → Home → Get Data → Text/CSV.
Select Superstore.csv → review the preview → Load.

7. Clean & Transform (Power Query)
Remove duplicate rows and handle missing values
Rename columns to business-friendly names
Fix data types (dates, decimals, whole numbers)
Add calculated columns (e.g., Profit Margin = Profit / Sales)

9. Data Modeling
One-to-many relationships: Customers → Orders, Products → Orders
Dedicated DateTable (marked as the official Date table) linked to both Orders and the Superstore file
Shared CategoryDim table connecting the flat file to the model via Category (star schema)

11. DAX Measures
DAX
Total Sales      = SUM('retail_analytics orders'[Sales])
Total Profit     = SUM('retail_analytics orders'[Profit])
Profit Margin %  = DIVIDE([Total Profit], [Total Sales], 0)
Total Orders     = COUNTROWS('retail_analytics orders')
Avg Order Value  = DIVIDE([Total Sales], [Total Orders], 0)

13. Build the Dashboard
KPI cards — Total Sales, Total Profit, Total Orders, Profit Margin %
Customer Analysis — segment donut chart + top-customers ranking
Product Analysis — category/sub-category chart + top-products ranking
Regional map — sales by state/city
Monthly trend line — sales & profit over time
Slicers — Year/Month, Category, State, Ship Mode

📊 Key Insights
Metric	Value
Total Sales	₹1,55,430
Total Profit	₹27,726.15
Profit Margin	17.84%
Total Orders	20
Avg Order Value	₹7,771.50

Technology is the top category (~56% of sales), led by the 27-inch LED Monitor and Laser Printer
Consumer and Corporate segments are almost evenly split (~40% each); Home Office is smallest (~20%)
Top 3 customers contribute ~39% of total revenue
Sales peaked in June (₹37,740); lowest in February (₹18,300)

🎓 Learning Outcomes
Designing and populating a relational MySQL database using SQL
Connecting Power BI to MySQL via the native connector
Importing and cleaning a flat file (CSV) from Kaggle
Building relationships and DAX measures in the data model
Designing an interactive, insight-driven Power BI dashboard

👤 Author
Prakruthi — BCA (AIML), Alliance University
