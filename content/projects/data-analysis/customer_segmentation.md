---
title: "🧑‍🤝‍🧑 UK Customer Segmentation"
date: 2025-06-30
description: "Behavioral segmentation of UK-based online retail customers using RFM features and unsupervised learning"
tags: ["customer segmentation", "clustering", "K-Means", "RFM", "data analysis"]
categories: ["Data Analysis"]
draft: false
---

## 🧠 Objective

Segment customers of a UK-based online gift retailer using transaction data to uncover behavior-driven groups for targeted marketing.

## 📦 Dataset

- Transactions from Dec 2010 to Dec 2011
- 541,909 records, 8 columns
- Key columns: InvoiceDate, Quantity, UnitPrice, CustomerID, Country

## 🔍 Methodology

1. **Data Wrangling**:  
   - Removed canceled orders and missing customer IDs  
   - Filtered out negative or zero Quantity and UnitPrice  
   - Parsed dates into datetime format

2. **Feature Engineering**:  
   - Built RFM features:  
     - *Recency*: Days since last purchase  
     - *Frequency*: Total purchases  
     - *Monetary*: Total amount spent  

3. **Preprocessing**:  
   - Log-transformed and scaled RFM values  
   - Applied PCA for 2D visualization  

4. **Clustering (K-Means)**:  
   - Determined optimal `k=3` using Elbow + Silhouette methods  
   - Assigned customers to 3 clusters  

5. **Visualization**:  
   - PCA scatter plot of clusters  
   - Boxplots and heatmap of RFM by cluster  
   - Choropleth map of customer countries  

## 🧩 Segment Profiles

| Cluster | Recency | Frequency | Monetary | Segment Type           |
|---------|---------|-----------|----------|-------------------------|
| 0       | Low     | High      | High     | 💎 Lapsed VIPs          |
| 1       | High    | Low       | Low      | 🧊 One-Time Buyers      |
| 2       | Medium  | Medium    | Medium   | ⏳ Mid-Tier Customers   |

## 🧠 Business Insight

- **Cluster 0**: High spenders, but inactive → win back with rewards or early access.
- **Cluster 1**: Likely one-time buyers → nudge with follow-ups or discounts.
- **Cluster 2**: Moderate engagement → develop into loyal customers with tailored campaigns.

## 🛠️ Tools

- Python (pandas, sklearn, seaborn, plotly)
- K-Means, PCA
- Jupyter Notebook

📓 [View Full Jupyter Notebook on GitHub](https://github.com/Bnjenga1/customer-segmentation-project/blob/main/uk_customer_segmentation.ipynb)
