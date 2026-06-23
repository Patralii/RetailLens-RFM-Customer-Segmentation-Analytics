
# RetailLens: RFM Customer Segmentation & Analytics

## 📌 Project Overview
E-commerce businesses often struggle with inefficient marketing spend by treating all customers equally. This project solves that problem by building a **Customer Segmentation Model** using **RFM Analysis** (Recency, Frequency, Monetary value). 

Built entirely in Microsoft Excel, this tool transforms raw, transactional data into actionable customer segments, enabling targeted marketing strategies like VIP loyalty rewards and churn-prevention campaigns.

## 🎯 Business Value & Impact
* **Identified High-Value Customers:** Segments "Champions" and "Loyal Customers" who drive the majority of revenue.
* **Churn Mitigation:** Highlights "At-Risk" customers who haven't purchased recently, allowing for targeted win-back campaigns.
* **Resource Optimization:** Shifts marketing focus from a blanket approach to data-driven, personalized engagement.

## 📊 The Dataset
**Source:** [Online Retail Dataset - UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/352/online+retail)
* **Size:** 541,909 rows, 8 columns.
* **Context:** Real-world transnational data for a UK-based non-store online retail dataset occurring between 01/12/2010 and 09/12/2011.

## 🛠️ Tools & Technologies
* **Microsoft Excel:** Data Cleaning, Advanced Formulas (`IF`, `XLOOKUP`), PivotTables, PivotCharts, Dashboarding.

## ⚙️ Methodology

### 1. Data Cleaning & Preparation
* Removed records with missing `CustomerID`s to ensure accurate user tracking.
* Filtered out negative quantities to exclude returns, refunds, and cancellations.
* Engineered a new `Total_Sales` feature (`Quantity` * `UnitPrice`) to calculate transaction revenue.

### 2. RFM Calculation
Created dynamic PivotTables to aggregate metrics at the unique `CustomerID` level:
* **Recency (R):** Days since the customer's last purchase relative to the most recent dataset date.
* **Frequency (F):** Total count of unique invoices per customer.
* **Monetary (M):** Sum of `Total_Sales` for each customer.

### 3. Scoring & Segmentation
* Applied percentile ranking to assign R, F, and M scores (1 to 5) to each customer.
* Concatenated the scores into a final RFM string (e.g., `555`, `111`).
* Built a logic matrix using `XLOOKUP` to map RFM scores to distinct business segments:
  * 🏆 **Champions:** Bought recently, buy often, and spend the most.
  * ⭐ **Loyalists:** Spend good money and buy often.
  * ⚠️ **At Risk:** Spent big money and purchased often, but haven't returned in a long time.
  * 💤 **Hibernating:** Last purchase was a long time ago, low spenders, and low number of orders.

Across customer segments, providing stakeholders with a clear view of product and customer health.
