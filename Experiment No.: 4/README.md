# ☕ Data Cleaning and Transformation of Cafe Sales Dataset using Power BI

## 📌 About the Project

This project focuses on **cleaning and transforming a Cafe Sales dataset using Power BI and Power Query**.

The raw dataset contained missing values, duplicate records, inconsistent entries, and placeholder values such as `ERROR` and `UNKNOWN`. The data was cleaned and transformed into a consistent and analysis-ready dataset using Power Query.

---

## 🎯 Objectives

* Import the raw Cafe Sales dataset into Power BI.
* Identify data quality issues.
* Handle missing and inconsistent values.
* Replace `ERROR` and `UNKNOWN` placeholders.
* Apply appropriate data types.
* Recover missing numeric values using calculations.
* Remove duplicate and unusable records.
* Clean and standardize text data.
* Prepare the dataset for further analysis and reporting.

---

## 🗂️ Dataset Information

**Dataset:** Cafe Sales Dirty Data for Cleaning Training

**Source:** Kaggle

**Original Records:** 10,000
**Columns:** 8

The dataset contains the following columns:

| Column           | Description                     |
| ---------------- | ------------------------------- |
| Transaction ID   | Identifier for each transaction |
| Item             | Cafe item purchased             |
| Quantity         | Number of items purchased       |
| Price Per Unit   | Price of one unit               |
| Total Spent      | Total amount spent              |
| Payment Method   | Payment method used             |
| Location         | Transaction location            |
| Transaction Date | Date of transaction             |

The dataset was intentionally used in its raw form because it contained missing values, duplicate records, and inconsistent placeholder entries.

---

## 🛠️ Technologies & Tools

* **Power BI Desktop**
* **Power Query**
* **CSV**
* **Kaggle Dataset**

---

## 🔄 Methodology

The data cleaning process was performed in **Power Query** through a series of transformations.

### 1. Import Raw Data

The `dirty_cafe_sales.csv` file was imported into Power BI using:

**Home → Get Data → Text/CSV → Transform Data**

All columns were initially kept as **Text** because the dataset contained mixed values and placeholders.

### 2. Handle Headers and Data Types

The first row was promoted as the column headers. The columns were then kept as Text until the placeholder values were cleaned.

### 3. Remove Placeholder Values

The following placeholder values were replaced:

* `ERROR` → Blank/Null
* `UNKNOWN` → Blank/Null

Keeping these as separate transformation steps made the cleaning process easier to review.

### 4. Apply Correct Data Types

After cleaning the placeholders, the appropriate data types were applied:

* **Quantity** → Whole Number
* **Price Per Unit** → Decimal Number
* **Total Spent** → Decimal Number
* **Transaction Date** → Date
* Other columns → Text

### 5. Recover Missing Numeric Values

Instead of deleting every row containing a missing numeric value, related columns were used to calculate the missing information.

**Missing Total Spent:**

```text
Total Spent = Quantity × Price Per Unit
```

**Missing Quantity:**

```text
Quantity = Total Spent ÷ Price Per Unit
```

**Missing Price Per Unit:**

```text
Price Per Unit = Total Spent ÷ Quantity
```

This helped preserve useful transaction records wherever the missing value could be calculated.

### 6. Handle Missing Text Values

Missing values in the following columns were replaced with meaningful labels:

* Item → `Unknown Item`
* Payment Method → `Unknown`
* Location → `Unknown`

The rows were preserved because the remaining transaction information could still be useful.

### 7. Remove Unusable Records

Rows with missing **Transaction Date** were removed because the date could not be reliably calculated from the available fields.

Rows where numeric values could not be recovered were also removed.

### 8. Remove Duplicate Records

Duplicate transactions were identified using:

* Item
* Payment Method
* Location
* Transaction Date
* Total Spent
* Quantity
* Price Per Unit

This helped identify repeated transaction records without relying only on Transaction ID.

### 9. Clean Text Data

The **Trim** transformation was used to remove unnecessary spaces from text values.

The **Clean** transformation was used to remove hidden or non-printable characters.

These steps helped maintain consistent text values for future grouping and analysis.

---

## 📊 Final Results

After completing all the transformations:

| Metric                      |  Result |
| --------------------------- | ------: |
| Original Records            |  10,000 |
| Final Records               |   9,272 |
| Records Removed             |     728 |
| Total Columns               |       8 |
| Duplicate Records Remaining |       0 |
| ERROR/UNKNOWN Placeholders  |       0 |
| Missing Transaction Dates   | Removed |

The final dataset contains **9,272 clean records** with appropriate data types and no remaining blank or placeholder values.

---

## 📈 Power Query Applied Steps

The major cleaning steps were renamed to make the transformation process easier to understand:

1. Source
2. Kept Raw Data as Text
3. Used First Row as Headers
4. Keep Columns as Text
5. Clear ERROR Values
6. Clear UNKNOWN Values
7. Apply Actual Data Types
8. Fix Missing Total Spent
9. Fix Missing Quantity
10. Fix Missing Price Per Unit
11. Remove Old Numeric Columns
12. Keep Original Column Names
13. Check Numeric Data Types
14. Filled Missing Item as `Unknown Item`
15. Filled Missing Payment Method as `Unknown`
16. Filled Missing Location as `Unknown`
17. Removed Rows with Missing Transaction Date
18. Remove Repeated Records
19. Remove Extra Spaces
20. Clean Hidden Characters
21. Remove Unusable Quantity or Total Spent Rows
22. Remove Unusable Price Per Unit Rows

Renaming the Applied Steps makes the Power Query workflow more readable and easier to review.

---

## 🎓 Learning Outcomes

Through this experiment, I learned:

* How to import CSV data into Power BI.
* How to use Power Query for data cleaning.
* How to identify data quality problems.
* How to handle missing and inconsistent values.
* How to apply correct data types.
* How to create custom columns using conditional logic.
* How to recover missing values using related columns.
* How to identify and remove duplicate records.
* How to use **Trim** and **Clean** transformations.
* How the order of Power Query transformations affects the final result.
* How to rename Applied Steps to create a clear and understandable workflow.

---

## ✅ Conclusion

This project demonstrates how **Power BI Power Query** can be used to transform a raw and inconsistent dataset into a clean and reliable dataset.

Missing values were recovered wherever possible, placeholder values were handled, duplicate records were removed, and text and data types were standardized.

The final dataset contains **9,272 records** and is ready for further **data analysis, visualization, and business reporting**.

---

## 👤 Author

**Prakruthi BR**
BCA – Artificial Intelligence & Machine Learning
Alliance University, Bengaluru

---

⭐ **If you find this project useful, feel free to star the repository!**
