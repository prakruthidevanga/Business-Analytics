# Sorting & Filtering Data in Power BI: High-Value Transactions and Underperforming Products

![Power BI](https://img.shields.io/badge/Tool-Power%20BI-F2C811?logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/Language-DAX-blue)
![Dataset](https://img.shields.io/badge/Data-Synthetic%20Excel-green)

A Business Analytics assignment (BCA, Semester V, Alliance University) that uses sorting and filtering techniques in Power BI to help a sales manager identify the company's **highest-value transactions** and **underperforming products**.

---



---

## Problem Statement
A sales manager wants to identify the company's highest-value transactions and underperforming products. Using sorting and filtering techniques in Power BI, extract the relevant business information and present it in an interactive dashboard.

## Dataset
- **File:** `data/sales_analysis_dataset.xlsx`
- **Main sheet used:** `Sales_Data`
- **Period:** October 2025 to September 2026
- **Size:** 300 transactions, 12 products, 3 categories, 4 regions, 8 salespeople, 15 customers
- **Note:** The data is synthetic and created for practice. It is not real company data.

| Column | Description |
|---|---|
| Transaction ID | Unique ID (TXN-1001 to TXN-1300) |
| Date | Date of sale |
| Region | East, North, South, West |
| Salesperson | Salesperson who made the sale |
| Customer | Customer name |
| Product | One of 12 products |
| Category | Hardware, Software, Services |
| Quantity | Units sold |
| Unit Price ($) | Selling price per unit |
| Discount % | Discount given |
| Unit Cost ($) | Cost per unit |
| Revenue ($) | Quantity × Unit Price × (1 − Discount %) |
| Profit ($) | Revenue − Quantity × Unit Cost |
| Returned | Y or N |

The workbook also contains helper sheets (Top_Transactions, High_Value, Product_Summary, Underperformers) with pre-built Excel versions of the results, used to verify the Power BI output.

## Tools Used
- Microsoft Power BI Desktop
- DAX (Data Analysis Expressions)
- Power Query
- Microsoft Excel (data source)



## Methodology
1. **Data collection:** Used the `Sales_Data` sheet of the Excel workbook.
2. **Data import:** Loaded the sheet with *Get Data → Excel workbook*, then *Transform Data → Close & Apply*.
3. **Data cleaning:** Checked for duplicates and missing values (none found; all 300 Transaction IDs are unique) and set correct data types for dates, numbers and percentages.
4. **DAX measures:** Created KPI measures, a high-value count and an underperforming flag (see below).
5. **Sorting and filtering:**
   - **Sort:** Transactions by Revenue (descending); products by Total Revenue (ascending).
   - **Top N filter:** Top 15 transactions by Revenue.
   - **Advanced filter:** Revenue ≥ $32,400 (about the 90th percentile) defines a high-value transaction.
   - **Visual-level filter:** Underperforming Flag = "Underperforming".
   - **Slicers:** Region, Category and Date.
6. **Dashboard:** Built a one-page interactive dashboard with KPI cards, tables and bar charts, and used red conditional formatting for underperforming products.

## DAX Measures
```DAX
Total Revenue = SUM(Sales_Data[Revenue ($)])

Total Profit = SUM(Sales_Data[Profit ($)])

Profit Margin % = DIVIDE([Total Profit], [Total Revenue])

Units Sold = SUM(Sales_Data[Quantity])

High Value Count =
CALCULATE(COUNTROWS(Sales_Data), Sales_Data[Revenue ($)] >= 32400)

Underperforming Flag =
-- Edit to match the rule you used in your dashboard
IF([Profit Margin %] < 0.15, "Underperforming", "OK")
```

## Dashboard
![Dashboard](screenshots/dashboard.png)

The dashboard contains:
- **KPI cards:** Total Profit, Total Revenue, Profit Margin %, High Value Count
- **Top 15 Transactions** table, sorted by revenue (highest first)
- **Total Revenue by Product** bar chart (lowest first)
- **Total Profit by Product** bar chart
- **Product table** with red highlighting for underperforming products
- **Slicers:** Region, Category, Date

## Key Results

| Metric | Value |
|---|---|
| Total transactions | 300 |
| Total revenue | $4,289,922 |
| Total profit | $1,706,242 |
| Profit margin | 39.8% |
| High-value transactions (≥ $32,400) | 32 |
| Revenue from high-value transactions | $1,187,172.50 (about 28% of total) |
| Top 15 transactions revenue | $714,200 (about 16.6% of total) |

### Top 5 transactions by revenue

| Rank | Product | Date | Region | Salesperson | Revenue | Profit |
|---|---|---|---|---|---|---|
| 1 | Enterprise CRM Suite | 05 Apr 2026 | South | Priya Nair | $48,000 | $28,000 |
| 2 | Onboarding Package | 18 Jun 2026 | North | Aisha Khan | $45,000 | $20,000 |
| 3 | Enterprise CRM Suite | 24 Feb 2026 | West | Sofia Rossi | $43,200 | $23,200 |
| 4 | Enterprise CRM Suite | 22 May 2026 | North | Aisha Khan | $43,200 | $23,200 |
| 5 | Onboarding Package | 07 Jan 2026 | East | Marcus Hill | $42,750 | $17,750 |

### Underperforming products

| Product | Category | Revenue | Profit | Margin |
|---|---|---|---|---|
| Legacy Fax Gateway | Hardware | $7,942.50 | −$1,077.50 | −13.6% |
| Basic Training Kit | Services | $26,970 | −$4,750 | −17.6% |
| Smart Display 55in | Hardware | $33,155 | −$6,445 | −19.4% |

## Insights and Recommendations
- **Enterprise CRM Suite** (10 of 32), **Business Laptop L5** (8) and **Onboarding Package** (7) account for most high-value transactions. Focus sales effort on these lines.
- **Analytics Platform** and **Enterprise CRM Suite** are among the most profitable products.
- Three products lose money: **Legacy Fax Gateway**, **Basic Training Kit** and **Smart Display 55in**. Review their pricing, discounts and costs, and consider discontinuing the weakest.
- **Wireless Router W2** is profitable (18% margin) but has low revenue compared with the other products, so it deserves monitoring.
- **West** is the strongest region by revenue ($1.22M); **East** is the lowest ($1.01M).

## How to Open the Project
1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Windows).
2. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   ```
3. Open `powerbi/sales_analysis.pbix`.
4. If Power BI cannot find the data, go to *Home → Transform data → Data source settings* and point it to `data/sales_analysis_dataset.xlsx`.

## Learning Outcomes
- Importing an Excel dataset into Power BI and setting data types
- Sorting data in ascending and descending order
- Applying Top N, advanced and visual-level filters
- Writing DAX measures for KPIs and conditional flags
- Using slicers and conditional formatting to build interactive dashboards
- Turning raw sales data into business insights

## Author
**Prakruthi BR**
Bachelor of Computer Applications, Semester V
Alliance University, Bengaluru


---
