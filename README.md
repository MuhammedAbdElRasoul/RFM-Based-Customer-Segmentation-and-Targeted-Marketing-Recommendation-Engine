# Customer Segmentation & RFM Analysis 🛒👥

An end-to-end data science project that segments e-commerce customers using **RFM Analysis** (Recency, Frequency, Monetary) and **K-Means Clustering**, paired with an automated **Targeted Marketing Recommendation Engine** to drive business growth.

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Key Features](#-key-features)
- [Dataset Summary](#-dataset-summary)
- [Methodology & Workflow](#-methodology--workflow)
- [Tech Stack](#-tech-stack)
- [Installation & Setup](#-installation--setup)
- [Cluster Insights & Recommendation Engine](#-cluster-insights--recommendation-engine)

---

## 🔍 Project Overview

Understanding customer behavior is essential for improving retention, maximizing customer lifetime value (CLV), and personalizing marketing strategies. 

This project transforms transaction-level online retail data into customer-level behavioral metrics:
1. **Recency (`Last_order`):** How recently a customer made a purchase (in days).
2. **Frequency (`Frequency`):** How many transactions the customer completed.
3. **Monetary Value (`Amount`):** Total amount spent by the customer.

Using these metrics, **K-Means Clustering** identifies meaningful customer groups, which are then passed into a recommendation function to automate targeted marketing campaigns.

---

## ✨ Key Features

* **RFM Feature Extraction:** Aggregates raw transactional data into customer-level behavioral features.
* **Outlier Removal:** Uses Interquartile Range (IQR) filtering on monetary value, transaction frequency, and recency to reduce extreme value skewness.
* **Feature Standardization:** Standardizes features using `StandardScaler` to ensure balanced distance calculations in clustering.
* **Optimal Cluster Selection:** Evaluates optimal $K$ value using both the **Elbow Method** (Inertia) and **Silhouette Scores**.
* **Cluster Visualization:** Plots scatter plots and box plots using Seaborn to interpret cluster boundaries and feature distributions.
* **Automated Recommendation Engine:** Maps generated customer clusters directly to tailored marketing strategies and promotions.

---

## 📊 Dataset Summary

The analysis uses the **Online Retail** dataset (`Online Retail.xlsx`), containing non-store online retail transactions.

* **Key Variables:**
  * `InvoiceNo`: Unique identifier for each transaction.
  * `CustomerID`: Unique identifier for each customer.
  * `Quantity` & `UnitPrice`: Used to calculate total spend (`Amount = Quantity * UnitPrice`).
  * `InvoiceDate`: Timestamp used to calculate purchase recency (`Last_order`).

---

## 🛠️ Methodology & Workflow

1. **Data Cleaning & Aggregation:**
   * Handled missing values and engineered total spend per transaction (`Amount`).
   * Grouped data by `CustomerID` to derive total monetary spend, transaction count (Frequency), and days since last purchase (Recency).
2. **Data Preprocessing & Outlier Filtering:**
   * Removed extreme outliers across `Amount`, `Frequency`, and `Last_order` using the $1.5 \times \text{IQR}$ rule.
   * Scaled numerical features using `StandardScaler`.
3. **Clustering & Evaluation:**
   * Iterated $K \in [2, 9]$ using `KMeans` to compute cluster inertia and silhouette scores.
   * Selected optimal $K = 3$ clusters based on evaluation metrics.
4. **Recommendation Mapping:**
   * Applied a dictionary-based mapping function (`get_recommendations`) to tag each customer with a targeted business action.

---

## 💻 Tech Stack

* **Language:** Python
* **Data Wrangling:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-Learn (`KMeans`, `StandardScaler`, `silhouette_score`)

---

## 📦 Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/customer-segmentation-rfm.git](https://github.com/your-username/customer-segmentation-rfm.git)
   cd customer-segmentation-rfm