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

### Pillar 1: Sales Performance Analysis (Revenue Perspective)

**Visualizations Used:** Stacked Column Chart and Pie Chart.

**Summary Metrics:** Total Revenue = $30,363 | Highest Revenue City = Chicago ($10,813) | Member Revenue Share = $17,614 (58%) vs. Normal Revenue Share = $12,749 (42%).

<p align="center">
  <img src="https://github.com/Teresa-Mingshu/MIS-311/blob/main/Pillar%201_Pie.png?raw=true" alt="Revenue Contribution by Customer Type" width="50%">
</p>

<p align="center">
  <img src="https://github.com/Teresa-Mingshu/MIS-311/blob/main/Pillar%201_Stacked.png?raw=true" alt="Sales Revenue by City" width="50%">
</p>

**Key Insight 1 (Market & Revenue Generation):**
The charts show that Chicago is the best city for sales (generating $10,813), and New York is second. Also, the revenue Pie Chart reveals that registered Members spend much more money than Normal customers, accounting for 58% ($17,614) compared to 42% ($12,749). This proves that the supermarket's membership program is working very well. The store should focus its marketing budget on keeping these high-value Members in Chicago.

### Pillar 2: Product & Inventory Analysis

**Visualizations Used:** Combo Chart, Histogram, and Box & Whisker Plot.

**Summary Metrics:** Top Category = Fruits ($7,450 with 632 items sold) | Lowest Category = Personal Care ($4,509 with 423 items sold).

<p align="center">
  <img src="https://github.com/Teresa-Mingshu/MIS-311/blob/main/Pillar%202_Combo.png?raw=true" alt="Product Category Performance Summary" width="80%">
</p>

<p align="center">
  <img src="https://github.com/Teresa-Mingshu/MIS-311/blob/main/Pillar%202_Histogram.png?raw=true" alt="Purchase Quantity Distribution" width="60%">
</p>

<p align="center">
  <img src="https://github.com/Teresa-Mingshu/MIS-311/blob/main/Pillar%202_Box%20Plot.png?raw=true" alt="Revenue Distribution and Outliers" width="70%">
</p>

**Key Insight 2 (Inventory & Supply Chain Optimization):**
The Combo Chart shows that Fruits is the best product group because it has both the highest total revenue ($7,450) and the highest quantity sold (632 items). On the other hand, Personal Care has the lowest revenue ($4,509) and the lowest quantity (423 items). The Histogram chart shows that customer order volumes are quite stable, usually around 10 or 16 items. Also, the Box Plot proves that transaction values have a very big variance, with big bulk orders stretching up to over $420 for Fruits and Stationery. From a supply chain view, the store must always keep enough "Fruits" in stock so it never runs out of stock (Safety Stock). For "Personal Care", the supermarket can reduce shelf space to save holding costs.

### Pillar 3: Customer Behavior Analysis (Store Operations Perspective)

**Visualizations Used:** Customer Purchasing Behavior Heatmap.

**Summary Metrics:** Top Member Category = Beverages ($4,850.79) | Top Normal Category = Household ($3,244.63) | Lowest Overall Category = Personal Care. Average Order Value (Mean) = $127 | Median Order Value = $107 | Most Common Single Purchase Value (Mode) = $38.63.

<p align="center">
  <img src="https://github.com/Teresa-Mingshu/MIS-311/blob/main/Pillar%203_Heatmap.png?raw=true" alt="Customer Purchasing Behavior Heatmap" width="60%">
</p>

**Key Insight 3 (Consumer Behavior & In-store Merchandising):**
The Heatmap chart shows a big difference in shopping habits between Member and Normal customers. Members spend the most money on Beverages ($4,850.79) and Fruits ($4,327.29) (these are the darkest red areas). However, Normal customers spend their money differently, mostly on Household ($3,244.63) and Fruits ($3,122.83). On the other hand, Personal Care has very low sales from both groups. Store managers can use this to arrange the store layout better. For example, they can put high-profit items next to the Fruits area or create special product combos for Members to make them buy more.

---

## 4. Conclusion & Recommendations

Based on the data analytics project, here are the final conclusions for the supermarket chain:

* **Target High-Value Hubs:** Chicago and New York are the main revenue drivers. The marketing team should focus their budget on these cities, especially targeting Member customers who contribute 58% of total sales.
* **Optimize SCM Inventory:** Fruits is a high-volume and high-revenue category, so the supply chain must always maintain a high Safety Stock. Personal Care is underperforming, so the store can reduce its shelf space to save holding costs.
* **Increase Basket Size:** Since the most frequent purchase value (Mode) is only $38.63, store managers should use cross-selling strategies. Putting high-profit items next to fast-moving items like Fruits and Beverages will help increase the average order value.

---

## 5. References

Eastern International University. (2026). *Supermarket sales dataset* [Data set]. Course materials for MIS 311: Introduction to Business Analytics. 

GitHub. (n.d.). *GitHub docs: Getting started with GitHub*. GitHub, Inc. https://docs.github.com/
