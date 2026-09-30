# SWYNEX | Cafe Sales Analysis Case Study

## Project Overview

This is an end-to-end cafe sales analytics project that combines data cleaning, exploratory data analysis, Excel-based business analysis, and an interactive Power BI dashboard.

The project follows the complete analytics workflow:

**Raw Data → Data Cleaning → Data Validation → Exploratory Analysis → Business Insights → Interactive Dashboard → Executive Findings**

The purpose of the final case study is to demonstrate how an initially inconsistent transactional dataset can be converted into a structured analytical dataset and then into business-facing insights.

---

## 1. Problem Statement

The cafe transaction dataset contained data quality issues that made direct analysis unreliable.

Key problems included:

- Missing values across several fields
- `ERROR` and `UNKNOWN` placeholders
- Numeric fields stored as text
- Missing payment methods
- Missing locations
- Invalid or missing transaction dates
- Missing item, quantity, price, and transaction values
- Potential high-value transactions that needed to be identified analytically

The business requirement was to clean the dataset, validate it, understand sales behavior, identify meaningful patterns, and create an interactive dashboard that could support business decision-making.

---

## 2. Project Objectives

The project was designed to:
`       
1. Clean and standardize the raw cafe transaction dataset.
2. Resolve missing, `ERROR`, and `UNKNOWN` values.
3. Convert analytical fields into usable numeric and date formats.
4. Validate the cleaned dataset.
5. Perform exploratory data analysis.
6. Identify product, payment, location, and monthly sales patterns.
7. Detect potential high-value transactions and outliers.
8. Build an interactive Power BI dashboard.
9. Convert analytical results into concise business insights.
10. Present the complete work as a reusable analytics case study.

---

## 3. Dataset Information

### Dataset

**Cafe Sales Transaction Dataset**

### Raw dataset size

- Rows: **10,000**
- Columns: **8**

### Raw columns

| Column | Description |
|---|---|
| Transaction ID | Unique identifier for each transaction |
| Item | Cafe product purchased |
| Quantity | Number of units purchased |
| Price Per Unit | Unit price of the selected item |
| Total Spent | Transaction-level spending amount |
| Payment Method | Method used for payment |
| Location | Sales channel/location |
| Transaction Date | Transaction date |

### Cleaned dataset size

- Rows: **10,000**
- Columns: **8**
- Date range: **2023-01-01 to 2023-12-31**
- Unique transaction IDs: **10,000**
- Duplicate rows after cleaning: **0**

The cleaned dataset preserves the **10,000 transaction records** while converting the fields into analysis-ready formats.

---

## 4. Data Cleaning and Preparation

The raw dataset was inspected for missing values, placeholders, invalid data types, and duplicated records.

### Raw data quality issues

The raw dataset contained:

- **6,826** blank/null cells across all columns
- **3,256** `ERROR`/`UNKNOWN` placeholder cells
- No duplicated rows in the raw dataset

### Invalid or incomplete records by field

| Field | Invalid / missing / placeholder records |
|---|---:|
| Item | 969 |
| Quantity | 479 |
| Price Per Unit | 533 |
| Total Spent | 502 |
| Payment Method | 3,178 |
| Location | 3,961 |
| Transaction Date | 460 |

### Cleaning rules applied

| Field | Cleaning approach used |
|---|---|
| Item | Invalid values replaced with the dominant valid category, **Juice** |
| Quantity | Invalid values standardized and filled with **3**, the central/mode value used in the cleaned data |
| Price Per Unit | Invalid values standardized and filled with **3.0** |
| Total Spent | Invalid values filled using the central transaction value used in the analysis, **8.0** |
| Payment Method | Invalid values replaced with the dominant category, **Digital Wallet** |
| Location | Invalid values replaced with the dominant category, **Takeaway** |
| Transaction Date | Invalid values filled with the dataset's modal date, **2023-07-02** |

The cleaned file was then converted to appropriate numeric and date data types for analysis.

### Validation

After cleaning:

- No missing values remained in the cleaned CSV.
- No duplicate rows remained.
- Transaction IDs remained unique.
- Quantity became integer type.
- Price Per Unit became floating-point numeric.
- Total Spent became floating-point numeric.
- Transaction Date was standardized to a valid date format.

### Data-quality limitation

The cleaning process focused primarily on missing, `ERROR`, and `UNKNOWN` values. Some rows that already contained numeric values remain arithmetically inconsistent with `Quantity × Price Per Unit`. Therefore, the dashboard analyzes the cleaned **Total Spent** field rather than silently rewriting every valid-looking transaction value.

---

## 5. Exploratory Data Analysis

The EDA workbook contains calculation tables and pivot analyses covering overall performance, product performance, payment behavior, location performance, and monthly revenue.

### Overall descriptive statistics

| Metric | Result |
|---|---:|
| Total Transactions | 10,000 |
| Total Revenue | $89,290.50 |
| Total Quantity Sold | 30,271 |
| Average Transaction | $8.93 |
| Median Transaction | $8.00 |
| Minimum Transaction | $1.00 |
| Maximum Transaction | $25.00 |
| Average Quantity per Transaction | 3.03 |
| Average Price per Unit | $2.95 |
| Transaction Standard Deviation | $5.99 |

### Distribution and outlier analysis

The exploratory analysis produced:

- Q1: **$4.00**
- Q3: **$12.00**
- IQR: **$8.00**
- Upper outlier boundary: **$24.00**
- Potential outliers: **268 transactions**

The outlier analysis identifies transactions above the Tukey upper bound as potential high-value transactions.

In the cleaned dataset, the 268 potential high-value transactions are **$25 transactions**, making them a distinct high-value segment for business analysis.

---

## 6. Product Analysis

### Revenue by product

| Rank | Product | Revenue | Share of Total |
|---:|---|---:|---:|
| 1 | Juice | $19,075.50 | 21.36% |
| 2 | Salad | $17,358.00 | 19.44% |
| 3 | Sandwich | $13,744.00 | 15.39% |
| 4 | Smoothie | $13,368.00 | 14.97% |
| 5 | Cake | $10,412.00 | 11.66% |
| 6 | Coffee | $7,100.00 | 7.95% |
| 7 | Tea | $4,980.00 | 5.58% |
| 8 | Cookie | $3,253.00 | 3.64% |

### Product findings

- **Juice** was the highest-revenue product with **$19,075.50**.
- Juice contributed **21.36%** of total revenue.
- Juice was also the highest-volume product with **6,435 units sold**.
- The top four products, Juice, Salad, Sandwich, and Smoothie, generated **71.16% of total revenue**.

---

## 7. Payment Method Analysis

| Payment Method | Revenue | Share |
|---|---:|---:|
| Digital Wallet | $48,354.00 | 54.15% |
| Credit Card | $20,483.00 | 22.94% |
| Cash | $20,453.50 | 22.91% |

### Finding

**Digital Wallet** was the dominant payment method, generating **$48,354** and contributing **54.15% of total revenue**.

---

## 8. Location / Channel Analysis

| Location | Revenue | Share |
|---|---:|---:|
| Takeaway | $62,039.00 | 69.48% |
| In-store | $27,251.50 | 30.52% |

### Finding

**Takeaway** generated **$62,039**, representing **69.48% of total revenue** and **6,983 transactions**.

---

## 9. Monthly Trend Analysis

Monthly revenue was analyzed across the 2023 calendar year.

| Month | Revenue |
|---|---:|
| January | $7,280.00 |
| February | $6,657.50 |
| March | $7,231.50 |
| April | $7,208.00 |
| May | $7,011.50 |
| June | $7,364.00 |
| July | $11,058.50 |
| August | $7,096.50 |
| September | $6,880.00 |
| October | $7,322.00 |
| November | $6,973.00 |
| December | $7,208.00 |

### Finding

**July** recorded the highest monthly revenue at **$11,058.50**, which was approximately **55.5% above the average revenue of the other months**.

---

## 10. High-Value Transaction Analysis

Potential high-value transactions were identified using the upper Tukey outlier boundary.

### High-value segment

- Potential high-value transactions: **268**
- Share of total transactions: **2.68%**
- High-value revenue: **$6,700.00**
- Share of total revenue: **7.50%**

### High-value revenue by product

- Salad: **$6,175.00**
- Juice: **$525.00**

**Salad accounted for approximately 92% of high-value transaction revenue.**

### Average transaction value by product

The highest average transaction value among products was recorded by **Salad at approximately $15.12**.

---

## 11. Power BI Dashboard

The final Power BI report contains **three interactive pages**.

### Page 1: Dashboard

The main dashboard provides a high-level performance view through:

- Total Revenue KPI
- Total Transactions KPI
- Total Quantity KPI
- Average Transaction Value KPI
- Average Quantity per Transaction KPI
- Revenue trend by date
- Revenue by product
- Quantity by product
- Revenue by payment method and location
- Revenue by location
- Interactive slicers

### Interactive filters

The dashboard supports filtering by:

- Item
- Date
- Payment Method
- Location
- Transaction Type

### Page 2: Business Insights

This page focuses on:

- Product revenue contribution
- Transaction type distribution
- Payment method revenue
- Highest month information
- Lowest month information
- Potential high-value transactions by item
- High-value transaction count
- High-value revenue
- High-value revenue percentage

### Page 3: Executive Insights

The Executive Insights page consolidates the ten core findings from the analysis.

---

## 12. Executive Business Findings

### Finding 1: Overall Performance

The cafe recorded **$89,290.50 in revenue** across **10,000 transactions** and sold **30,271 units**.

### Finding 2: Product Performance

**Juice** was the largest revenue contributor at **$19,075.50**, accounting for **21.36% of total revenue**.

### Finding 3: Revenue Concentration

**Juice, Salad, Sandwich, and Smoothie** together contributed approximately **71.16% of total revenue**.

### Finding 4: Sales Volume

**Juice** was also the highest-volume product with **6,435 units sold**.

### Finding 5: Payment Behavior

**Digital Wallet** generated **$48,354**, representing **54.15% of total revenue**.

### Finding 6: Location Performance

**Takeaway** generated **$62,039**, representing **69.48% of total revenue** and **6,983 transactions**.

### Finding 7: Monthly Performance

**July** generated the highest monthly revenue at **$11,058.50**, approximately **55.5% above the average revenue of the other months**.

### Finding 8: High-Value Transactions

Potential high-value transactions accounted for **2.68% of transactions** but contributed approximately **7.50% of total revenue**.

### Finding 9: High-Value Product Concentration

**Salad** accounted for approximately **92% of the revenue generated by potential high-value transactions**.

### Finding 10: Transaction Value

**Salad** had the highest average transaction value among products at approximately **$15.12**.

---

## 13. Business Problems Addressed

The project provides a structured response to these business questions:

- What is the overall revenue and sales volume?
- Which products contribute the most revenue?
- Which products sell the highest number of units?
- Which payment method contributes the most revenue?
- Which sales channel/location performs best?
- Which month produces the highest revenue?
- How concentrated is revenue across products?
- How significant are potential high-value transactions?
- Which products dominate high-value revenue?
- Which products have the highest average transaction value?
- How can management explore these metrics interactively?

---

## 14. Tools and Technologies

### Data preparation

- Python / Pandas
- CSV data cleaning
- Data type conversion
- Missing-value handling
- Placeholder-value handling

### Exploratory analysis

- Microsoft Excel
- Pivot tables
- Descriptive statistics
- Outlier analysis
- Monthly aggregation
- Product and payment analysis

### Dashboard development

- Microsoft Power BI
- DAX
- Data modeling
- KPI cards
- Interactive slicers
- Bar charts
- Column charts
- Line charts
- Donut / pie charts
- Executive insight page

---

## 15. Project Deliverables

The complete work is organized across three GitHub repositories.

### Data Cleaning and Preparation

https://github.com/Rico-04-CSE/SWYNEX-Data-Cleaning-Preparation

### Exploratory Data Analysis

https://github.com/Rico-04-CSE/SWYNEX-Exploratory-Data-Analysis

### Interactive Cafe Sales Dashboard

https://github.com/Rico-04-CSE/SWYNEX-Interactive-Cafe-Sales-Dashboard

---

## 17. End-to-End Workflow

```text
Raw Cafe Sales Dataset
        |
        v
Data Quality Assessment
        |
        v
Missing / ERROR / UNKNOWN Handling
        |
        v
Data Type Standardization
        |
        v
Cleaned Transaction Dataset
        |
        v
Exploratory Data Analysis
        |
        v
Product / Payment / Location / Monthly Analysis
        |
        v
Outlier and High-Value Analysis
        |
        v
Power BI Data Model
        |
        v
Interactive Dashboard
        |
        v
Executive Business Insights
```

---

## 18. Author Authentication

**Project:** SWYNEX Final Analytics Case Study  
**Author / GitHub Identity:** `Pritam Dey` / `Rico-04-CSE`  

This case study consolidates the supplied data-cleaning, exploratory-analysis, and Power BI dashboard work into one end-to-end analytics project.

The calculations, findings, cleaning statistics, and dashboard observations documented here are based on the supplied project files and the associated SWYNEX repositories.

---

## 19. Final Submission

### Project URL

https://github.com/Rico-04-CSE/SWYNEX-Interactive-Cafe-Sales-Dashboard

### Supporting URLs

Data Cleaning and Preparation:  
https://github.com/Rico-04-CSE/SWYNEX-Data-Cleaning-Preparation

Exploratory Data Analysis:  
https://github.com/Rico-04-CSE/SWYNEX-Exploratory-Data-Analysis

---

## 20. Conclusion

The SWYNEX project demonstrates a complete analytics lifecycle from raw transactional data to business-facing decision support.

The final solution combines:

- Data cleaning
- Data validation
- Exploratory analysis
- Descriptive statistics
- Outlier detection
- Product analysis
- Payment analysis
- Location analysis
- Monthly trend analysis
- High-value transaction analysis
- Interactive Power BI reporting
- Executive business insights

The project shows how structured analytics can turn a messy transaction file into an interactive business intelligence solution that communicates performance clearly and supports practical decision-making.
