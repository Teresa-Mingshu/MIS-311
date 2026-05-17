# Supermarket Sales Intelligence: Transforming Transactional Data into Operational Insights

## 1. Data Overview

### Context and Objective
The analysis aims to examine historical retail transaction records across different supermarket branches to understand consumer purchasing behavior and operational efficiency. The dataset includes information on branch locations, customer types, product classifications, quantities purchased, and transaction values, with the total price serving as the primary financial metric. This insight is critical for optimizing supply chain logistics, inventory management, and regional marketing strategies.

### Key Variables
* **Sale ID:** Unique identification number assigned to each individual transaction.
* **Branch:** The specific supermarket outlet where the sales occurred (Branch A or B).
* **City:** The geographical location of the branch (New York, Los Angeles, and Chicago).
* **Customer Type:** Segmentation of shoppers based on loyalty status (Member or Normal).
* **Product Name:** The specific item purchased during the transaction.
* **Product Category:** The broader classification of the merchandise (e.g., Personal Care, Stationary, Household, Food and beverages).
* **Quantity:** The total number of items bought per transaction line.
* **Total Price:** The gross financial revenue generated from the sale (dependent variable).

### Sources of the Data
The dataset is sourced from the supermarket's Point of Sale (POS) system, provided officially by the instructor for the MIS 311 course folder on Moodle (EIU).

### Initial Structure
* **Number of Columns:** 8 columns
* **Number of Rows:** 254 rows (including the header) found in the raw Excel sheet.

---

## 2. Data Cleaning

Before conducting the analysis, the dataset was checked for missing values, duplicate rows, and formatting issues to improve data quality and reliability.

* **Missing Values:**
A total of **6 missing values** were identified across `customer_type`, `product_category`, and `quantity`. Instead of using Mode Imputation — which could cause logical mismatches (e.g., assigning "Fruits" category to a "Shampoo" product) — these incomplete rows were **permanently removed**. This ensures 100% data integrity and logical consistency for subsequent Pivot Table analysis.

* **Duplicate Rows:**
A total of **3 duplicate rows** were identified and removed based on the unique key `sale_id` to ensure consistency and prevent double-counting errors in the analysis.

* **Data Types:**
  * **Numerical columns:** quantity, total_price
  * **Categorical columns:** sale_id, branch, city, customer_type, product_name, product_category

* **Outlier Analysis:**
The `total_price` column showed some unusually high transaction values. These outliers were retained in the dataset because they represent genuine, large-volume retail purchases that are critical for realistic supply chain and revenue forecasting.

### Data Cleaning Summary
After cleaning and preprocessing, the final dataset contained 250 rows and 8 columns ready for analysis.

---

## 3. Descriptive Analysis

### Baseline Data Profile

The summary table below presents the descriptive statistics for the continuous numerical variables (`quantity` and `total_price`) to establish a foundational baseline for the dataset.

<p align="center">
  <img src="https://github.com/Teresa-Mingshu/MIS-311/blob/main/Descriptive%20Statistics.png?raw=true" alt="Descriptive Statistics Table" width="60%">
</p>

### Data Interpretation

The descriptive statistics table highlights key characteristics of the store's sales dynamics:

* **Sales Consistency (`quantity`):** With a Mean of **10.8** items and a Mode of **10**, customer order volumes are highly consistent and predictable, simplifying checkout management and SCM load planning.
* **Revenue Volatility (`total_price`):** Transaction values show extreme variance (Standard Deviation = **$102.80**), stretching from a minimum of **$2.18** to a bulk purchase maximum of **$427.14**.
* **Median vs. Mode Gap:** While the Median order value is **$106.59**, the most frequent basket value (Mode) is only **$38.63**. This gap reveals that the store relies on frequent, small daily convenience purchases for steady foot traffic, while overall revenue is heavily driven upward by occasional high-value bulk orders (Outliers).



