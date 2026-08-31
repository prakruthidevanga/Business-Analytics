
# Superstore Sales Performance Analysis — Power BI

A Power BI dashboard project analyzing sales, profit, and discount patterns across products, categories, and regions using the Sample Superstore dataset. Built as part of a Business Analytics assignment (BCA, Semester V, Alliance University).

## 📌 Overview

Retail businesses generate huge volumes of transactional data every day, but raw spreadsheets rarely tell a clear story on their own. Management at this fictional superstore needed a fast, visual way to understand how sales and profit were performing — not just overall, but broken down by product category, sub-category, customer segment, shipping method, and geographic region.

This project takes the Sample Superstore dataset and turns it into a fully interactive Power BI dashboard. The process covers the complete analytics workflow: importing raw data, cleaning and transforming it, building a proper data model with time intelligence, writing reusable DAX measures, and designing a 3-page report that highlights the patterns that actually matter for decision-making — most importantly, how discounting behavior is quietly eating into profit on certain products.

## 📂 Dataset

- **Source:** [Sample Superstore Dataset — Kaggle](https://www.kaggle.com/datasets/naveenkumar20bps1137/sample-superstore)
- **Size:** ~9,994 records, 13 fields
- **Key fields:** Order Date, Ship Date, Ship Mode, Segment, Region, State, City, Category, Sub-Category, Product Name, Sales, Quantity, Discount, Profit
- **Nature of data:** Order-level retail transaction records, spanning multiple years, covering three product categories (Furniture, Office Supplies, Technology) sold across four US regions.

## 🛠️ Tools Used

- **Power BI Desktop** — dashboard design and data modeling
- **Power Query Editor** — data cleaning and transformation
- **DAX (Data Analysis Expressions)** — measures and time-intelligence calculations
- **Kaggle** — dataset source

## 🔧 Project Workflow

1. **Data Collection** — Sourced the Sample Superstore dataset from Kaggle in CSV format, containing order-level transaction data across three years.
2. **Data Import** — Loaded the CSV into Power BI Desktop via Get Data → Text/CSV, then opened it in Power Query Editor for review before any transformations.
3. **Data Cleaning & Transformation** — Corrected inconsistent date formats on Order Date and Ship Date, set proper data types across all numeric fields (Sales/Profit/Discount as decimals, Quantity as whole numbers), removed duplicate rows based on Row ID, checked for and handled missing values, and renamed columns for clarity.
4. **Data Modeling** — Built a dedicated Date table using DAX's `CALENDAR()` function instead of relying on the raw Order Date column directly, added Year/Month/Month Name/Quarter columns to support time-based grouping, marked it as the official Date Table, and created a relationship between the Date table and Order Date to enable accurate time-intelligence calculations.
5. **DAX Measures** — Wrote a set of reusable measures (Total Sales, Total Profit, Profit Margin %, Total Orders, Average Discount, Total Quantity, Sales Prior Year, Sales YoY %) so every visual across the report pulls from the same consistent calculations instead of repeating logic.
6. **Dashboard Development** — Designed three report pages with KPI cards, bar/line/scatter charts, a color-coded map, interactive slicers, and a consistent color theme and formatting applied across all pages for a polished, presentation-ready look.

## 📊 Report Pages

### 1. Executive Overview
The entry point of the report, designed to answer "how is the business doing overall?" before drilling into deeper detail. Includes four KPI cards (Total Sales, Total Profit, Profit Margin %, Total Orders) for an instant performance snapshot, a monthly Sales vs. Profit trend line that reveals seasonal peaks, a filled map showing sales concentration by state, and slicers for Year, Category, Region, and Segment so the entire page can be filtered dynamically without needing separate reports.

### 2. Category & Product Performance
Goes a level deeper than the Overview page, focusing on individual products and sub-categories. A bar chart of Sales by Sub-Category identifies the strongest and weakest product lines. A scatter chart plotting Profit against Discount by Sub-Category is the key analytical visual here — it exposes exactly where heavy discounting is cutting into margin. A Category → Sub-Category table lays out Sales, Profit, and Profit Margin % side by side for easy comparison, and a Top 10 Products table highlights the best-selling individual items for inventory and marketing prioritization.

### 3. Regional Analysis
Shifts the focus to geography and customer segments. A filled map colored red-to-green by profit makes it immediately obvious which states are actually losing money, even when their sales figures look healthy. A clustered column chart breaks down Sales by Region while further splitting each bar by customer Segment. A bar chart shows which shipping method (Standard, Second, First Class, Same Day) is used most, and a donut chart shows the proportional revenue contribution of each customer segment.

## 💡 Key Insights

- Sales consistently peak in November–December, likely driven by holiday shopping demand.
- A small number of sub-categories account for a disproportionately large share of total revenue, following a classic 80/20 pattern.
- Tables and Bookcases show high sales volume but low or negative profit, driven by discounts consistently above 30%.
- There is a clear, visible negative relationship between discount level and profit — the more an item is discounted, the less profitable it becomes.
- Several states show strong sales figures but still operate at a net loss once discounting is factored in.
- The West and East regions are generally the most profitable, while parts of the Central region show weaker or negative profit.
- The Consumer segment generates the highest total sales volume, but Corporate and Home Office segments often carry better profit margins per order.
- Standard Class is by far the most frequently used shipping mode, which has direct implications for fulfillment cost planning.
- Comparing Sales YoY % helps distinguish genuine year-over-year growth from normal seasonal fluctuation.

## 📈 DAX Measures Used

```DAX
Total Sales = SUM(Superstore[Sales])
Total Profit = SUM(Superstore[Profit])
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)
Total Orders = DISTINCTCOUNT(Superstore[Order ID])
Average Discount = AVERAGE(Superstore[Discount])
Total Quantity = SUM(Superstore[Quantity])
Sales Prior Year = CALCULATE([Total Sales], SAMEPERIODLASTYEAR(DateTable[Date]))
Sales YoY % = DIVIDE([Total Sales] - [Sales Prior Year], [Sales Prior Year], 0)
```

Each measure serves a specific analytical purpose: `Total Sales` and `Total Profit` form the core performance metrics, `Profit Margin %` expresses profitability as a ratio (using `DIVIDE()` to safely avoid divide-by-zero errors), `Total Orders` counts distinct orders rather than line items, `Average Discount` supports the discount-vs-profit analysis, and `Sales Prior Year` / `Sales YoY %` rely on the Date table relationship to enable accurate time-intelligence comparisons.

## 🚀 How to Use

1. Clone this repository to your local machine.
2. Open the `.pbix` file in Power BI Desktop (free download from Microsoft).
3. Use the slicers on each page — Year, Category, Region, Segment — to filter and explore the data interactively.
4. Hover over any chart or map to see detailed tooltips with exact values.
5. Navigate between the three report pages using the tabs at the bottom of the window.

## 🎓 Learning Outcomes

- Learned how to import, clean, and transform real-world CSV data using Power Query, including fixing inconsistent formats and handling duplicates.
- Understood the importance of building a dedicated Date table and enabling proper time-intelligence functionality in Power BI.
- Gained hands-on experience writing DAX measures using SUM, DISTINCTCOUNT, DIVIDE, CALCULATE, and SAMEPERIODLASTYEAR.
- Learned to design and format a range of interactive visuals — KPI cards, line charts, bar charts, scatter charts, maps, and matrices.
- Practiced applying consistent themes, colors, and formatting choices to produce a professional, presentation-ready report.
- Learned to translate raw data patterns — like the discount-vs-profit relationship — into clear, actionable business insights for decision-makers.
- Improved overall end-to-end proficiency in Power BI, from raw data import through to a finished, interactive business dashboard.

## 👤 Author

**Prakruthi BR**
BCA, Semester V — Business Analytics
Alliance University
