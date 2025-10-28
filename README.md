## Introduction
In today's highly competitive e-commerce landscape, understanding customers beyond demographic data is the key to survival and growth. Few companies collect amounts of transaction data daily, but often fail to leverage the data to build stronger relationships with customers.

A "one-size-fits-all" marketing approach is no longer efficient, costly, and often irrelevant. To remain competitive, companies must shift from mass marketing to a more personalized strategy. Customer segmentation plays a key role. By grouping customers based on their behavior, companies can send the right message, to the right person, at the right time.

The primary goal of this project is to segment customers in an online retail dataset. The specific objectives are:
1. Identify a meaningful customer segments based on their purchasing behavior (Recency, Frequency, and Monetary).
2. Analyze the unique characteristics of each segment (e.g., Which segment is the best customer? Which segment is at risk of churning? Which segment is already "lost"?).
3. Provide personalized business and marketing strategy recommendations for each segment to increase loyalty, retention, and Customer Lifetime Value (CLV).

## RFM Overview
To understand customer behavior, the method used is Recency, Frequency, and Monetary (RFM) analysis. RFM is a simple yet powerful model that assesses each customer based on three dimensions:
1. R (Recency): When was the last time the customer made a transaction? Customers who have recently purchased tend to be more responsive.
2. F (Frequency): How often does a customer make a transaction within a given period? Customers who frequently purchase are more loyal.
3. M (Monetary): How much money does a customer spend in total? Customers who spend a lot of money are high-value customers.

To perform RFM, the dataset must have some crucial features:
1. Customer ID: A unique identifier for each customer to differentiate between customers.
2. Transaction Date: Date and time the transaction were made to calculate the Recency component.
3. Transaction Value: The total amount spent by customer.

## Project Workflow
The project is devided into few steps:
1. **Data loading**: Load the "_Online Retail.csv_" dataset. (can be accesed through https://www.kaggle.com/datasets/vijayuv/onlineretail)
2. **Data Cleaning**:
   * Drop the missing values on "CustomerID".
   * Drop the canceled or the unreal values on "Quantity" and "UnitPrice".
   * Drop the duplicated rows.
   * Change the "InvoiceDate" to datetime format.
3. **Feature Engineering**: Create the three main features for each customer:
   * Recency (R): Days passed since the last transaction.
   * Frequency (F): Customer's rate of transactions.
   * Monetary (M): Total spent each customers.
4. **Data Transformation**:
   * Apply the **Log Transform** to normalize data distribution.
   * Using **StandardScaler** to standardize the scale of all features.
5. **Modeling - K-Means**:
   * Using the Elbow Method to determine the optimal number of clusters (k).
   * **k=4** was chosen as the ideal number of clusters to obtain detailed yet actionable insights.
6. **Analysis and Visualization**:
   * Analyze the average R, F, and M values ​​for each cluster.
   * Create visualizations (Boxplot, Pairplot, Bar chart) to illustrate the findings.

## Analysis Results
Based on $k=4$, the customer are clustered into 4 segments that are:
1. **Cluster 2: VIP Customers**
   * Characteristics: **Lowest** recency, **Highest** frequency and monetary.
   * Analysis: **The best** customer segment, recently shopped, very frequently, and spent the most money.
   * Quantity: 864 customers (19.9%)
2. **Cluster 0: Loyal Customers**
   * Characteristics: **Quite low** recency, **Average** frequency and monetary.
   * Analysis: **The second largest** group and concistently shop. **The main/core** of the business.
   * Quantity: 1222 customers (28.2%)
3. **Cluster 1: At-Risk Customers**
   * Characteristics: **Quite high** recency, **Low** frequency and monetary.
   * Analysis: The customers haven't purchased in several months. They are at high risk of churn if not re-"activated" immediately.
   * Quantity: 870 customers (20.1%)
4. **Cluster 3: "Lost" Customers**
   * Characteristics: **Highest** recency, **Lowest** frequency and monetary.
   * Analysis: The customers haven't purchased in a long time and most likely will not purchased in the future.
   * Quantity: 1382 customers (31.9%)

## Business Recommendation
Based on the results, here are the actionable marketing strategies:
| Persona | Strategi | Aksi yang Direkomendasikan |
| :--- | :--- | :--- |
| **VIP Customers** | **Appreciate & Maintain** | Provide exclusive loyalty programs, early access to new products, rewards, and priority services. |
| **Loyal Customers** | **Engage and Enhance** | Offer product bundling and discounts on next purchases (upsell). |
| **At-Risk Customers** | **Re-Activate** | Send a "We Miss You!" campaign with a special discount or free shipping offer to entice them back. |
| **"Lost" Customers** | **Minimum Effort** | Send one final "win-back" campaign. If there's no response, remove them from the active email list to save costs. |
