# E-commerce Customer Retention Project

## 📌 Project Overview

This project analyzes transaction-level e-commerce data from a Turkish online retail platform to understand customer behavior and retention patterns. The primary goal is to identify customers likely to return and make multiple purchases within six months, enabling the business to focus on profitable retention strategies. Retaining existing customers is significantly more cost-effective than acquiring new ones.

The workflow includes:

* Data preparation & feature engineering – transforming raw data into a structured customer-level dataset. For purpose of predicting retention, only the details of customer's first purchase are kept in a transformed dataset.

* Exploratory Data Analysis (EDA) – uncovering patterns, trends, and behavioral drivers of retention, for transaction and customer level data.

* Retention-focused insights – guiding predictive modeling and strategic decision-making, based on the results of the previous sections.

## 🎯 Project Goals

The goal is to build a predictive dataset for customer retention, understand what drives customers to purchase multiple times, and identify high-value customers to target for business strategies.

## 📊 Dataset Overview

Data Source: Kaggle – E-Commerce Customer Behavior & Sales Analysis -TR (found on the link https://www.kaggle.com/datasets/umuttuygurr/e-commerce-customer-behavior-and-sales-analysis-tr)

* Records: 5,000 transactions
* Date Range: 01 Jan 2023 – 26 Mar 2024
* Features: 18 columns covering order details, customer demographics, product info, transaction metrics, behavior, and post-purchase ratings.

| Category       | Features |
|----------------|---------|
| Order Info     | Order_ID, Date |
| Customer       | Customer_ID, Age, Gender, City |
| Product        | Product_Category, Unit_Price, Quantity |
| Transaction    | Discount_Amount, Total_Amount, Payment_Method |
| Behavior       | Device_Type, Session_Duration_Minutes, Pages_Viewed, Is_Returning_Customer |
| Post-Purchase  | Delivery_Time_Days, Customer_Rating |


## 🛠 Data Preparation Highlights

* Cleaning & Enrichment: Added temporal columns (Year, Month, Quarter, Weekday) for context and richness. Outliers are retained as they reflect meaningful customer behavior, not the error or inconsistency in the data.

* First Purchase Aggregation: Aggregated the data on the customer ID for the first purchase, and combined multiple purchases on the first day to ensure one row per customer while preserving key engagement signals. Multiple first-day purchases are rare, just about 0.48% of customers made 2 or more of those purchases.

* Feature Handling: Numerical features are aggregated (sum/mean) to capture total values and typical (average) customer behavior. Categorical features (e.g., product category, payment method, device type) are captured from the most expensive purchase to preserve strongest behavioral signal.

* Retention Definition: Defined `Retention = 1` if a customer placed ≥3 orders within six months of their first purchase.

* Retention distribution:  roughly balanced (50:50), making it suitable for modeling. 

## 🔍 EDA & Key Insights

#### Transaction-Level Insights:

* Revenue is volume-driven rather than AOV-driven.

* Electronics dominate revenue due to higher unit prices, despite similar order counts across categories.

* Small and moderate discounts (0–20%) are associated with higher retention; very high discounts (20–30%) are negligible (~6 customers) and can’t be interpreted meaningfully.

* Mobile devices account for the majority of transactions, highlighting the importance of mobile optimization.

#### Customer-Level Insights:

* Retention is frequency-driven: repeat purchases are the strongest indicator.

* Recency alone doesn’t guarantee loyalty; frequent buyers are retained regardless of recent activity.

* Mid-tier customers (RFM 5–6) represent the biggest growth opportunity.

* High revenue does not always equal loyalty.

* Behavioral metrics like session duration and pages viewed have limited impact on retention.

### Strategic Takeaways:

* Focus on converting occasional buyers into repeat buyers.

* Nurture mid-frequency segments (RFM 5–6) to increase lifetime value.

* Prioritize high-volume cities and payment/device segments for maximum retention impact.


## Future Steps

Currently, this project contains only data preparation and exploratory data analysis. Planned next steps include:

* **Feature Engineering** – Create new features from customer behavior, temporal patterns, and purchase history to improve predictive power.

* **Model Selection** – Test predictive models for retention, starting with logistic regression and tree-based methods (e.g., Random Forest or XGBoost).

* **Model Evaluation** – Split the data into training and test sets, tune hyperparameters, and evaluate performance using metrics like accuracy, ROC-AUC, and F1-score.

* **Insights & Strategy** – Use model results to identify high-potential customers and inform retention strategies.