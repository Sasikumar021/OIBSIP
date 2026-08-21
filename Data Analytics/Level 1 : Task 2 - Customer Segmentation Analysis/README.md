# E-Commerce Customer Segmentation Analysis

An end-to-end data analytics project that applies RFM (Recency, Frequency, Monetary) modeling and K-Means clustering to segment an e-commerce customer base. The analysis identifies distinct customer purchasing behaviors to enable targeted, data-driven marketing strategies.

---

## 📌 Project Overview

Understanding customer purchasing patterns is critical for targeted marketing and customer retention. Using historical e-commerce transactional data, this project aggregates line-item transactions into customer-level behavioral metrics and groups customers into actionable clusters using machine learning.

### Objectives
* Load, clean, and preprocess raw transaction data (handle missing values, remove invalid orders).
* Calculate key descriptive statistics (Average Purchase Value, Frequency, Customer Lifetime Value).
* Engineer **RFM features** (Recency, Frequency, Monetary) per customer.
* Standardize data using logarithmic transformation and `StandardScaler`.
* Determine optimal cluster count ($K$) using the **Elbow Method** and **Silhouette Analysis**.
* Segment customers using **K-Means Clustering**.
* Visualize cluster distributions across feature pairs.
* Provide strategic marketing recommendations tailored to each customer segment.

---

## 🛠️ Tech Stack

* **Language:** Python
* **Environment:** Jupyter Notebook / Google Colab
* **Libraries:**
  * **Data Manipulation:** `pandas`, `numpy`
  * **Machine Learning:** `scikit-learn` (`KMeans`, `StandardScaler`, `silhouette_score`, `silhouette_samples`)
  * **Data Visualization:** `matplotlib`, `seaborn`

---

## 📊 Dataset

* **Source:** [Online Retail Dataset]((https://www.kaggle.com/datasets/ulrikthygepedersen/online-retail-dataset) (Kaggle)
* **Description:** Contains all transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based non-store online retail firm.

---

## 📈 Methodology & Workflow

1. **Data Cleaning & Preprocessing:**
   * Removed records missing `CustomerID`.
   * Filtered out returns/cancelled orders (`Quantity > 0` and `UnitPrice > 0`).
   * Created total spending per item (`TotalSum = Quantity * UnitPrice`).

2. **RFM Feature Engineering:**
   * **Recency ($R$):** Days since the customer's last purchase.
   * **Frequency ($F$):** Number of unique transactions made.
   * **Monetary ($M$):** Total money spent by the customer.

3. **Feature Transformation & Scaling:**
   * Log transformation (`np.log1p`) to eliminate severe positive skewness.
   * `StandardScaler` to ensure features are scaled to mean = 0, variance = 1.

4. **Clustering & Validation:**
   * **Elbow Method:** Plot Within-Cluster Sum of Squares (WCSS / Inertia).
   * **Silhouette Analysis:** Evaluated average and per-cluster silhouette scores to confirm optimal $K=4$.

---

## 🎯 Customer Segments & Marketing Strategy

| Cluster Label | Segment Type | Behavioral Profile | Recommended Strategy |
| :--- | :--- | :--- | :--- |
| **Cluster 0** | **Recent / New Customers** | Low Recency, Low Frequency, Moderate Spend | Onboarding series, early-bird discounts to drive 2nd purchase. |
| **Cluster 1** | **Champions / VIPs** | Low Recency, High Frequency, High Spend | VIP loyalty perks, early access to new products, dedicated support. |
| **Cluster 2** | **At-Risk Customers** | Moderate Recency, Moderate Frequency, Moderate Spend | Re-engagement campaigns, personalized recommendations based on history. |
| **Cluster 3** | **Hibernating / Lost** | High Recency, Low Frequency, Low Spend | Win-back discount codes; minimize ad spend if non-responsive. |
