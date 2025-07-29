# 🚕 Clustering NYC Taxi Trips using Gaussian Mixture Models (GMM)

This project applies unsupervised machine learning techniques to discover patterns in real-world NYC taxi ride data using **Gaussian Mixture Models (GMM)**.

---

## 📊 Project Objective

Segment NYC taxi trips into distinct groups (clusters) based on trip characteristics such as:
- Number of passengers
- Distance and duration
- Fare and tip amount
- Time of pickup

This enables better understanding of customer behaviors, ride types, and potential anomalies — all without labeled data.

---

## 📂 Dataset

- **Source**: [NYC Yellow Taxi Trip Dataset on Kaggle](https://www.kaggle.com/datasets/elemento/nyc-yellow-taxi-trip-data?select=yellow_tripdata_2016-02.csv)
- **Size**: 100,000+ taxi ride records
- **Key Columns Used**:
  - `passenger_count`
  - `trip_distance`
  - `fare_amount`
  - `tip_amount`
  - `total_amount`
  - `trip_duration` (engineered from timestamps)
  - `pickup_hour` (engineered from pickup time)

---

## 🧹 Data Preparation Steps

1. Load CSV dataset
2. Filter out outliers and incomplete rows
3. Engineer new features:
   - `trip_duration` from `pickup` and `dropoff` timestamps
   - `pickup_hour` from timestamp
4. Select and scale features for clustering

---

## 🤖 Model: Gaussian Mixture Models (GMM)

- GMM allows **soft clustering** (each trip has probabilities for each cluster).
- More flexible than KMeans for real-world, overlapping data.
- We selected the number of clusters (k=3) using silhouette scores.

  
Imagine you have a dataset of points, and you believe that these points are generated from several different groups (clusters). But instead of hard boundaries like K-Means (where each point belongs to only one cluster), you want soft boundaries, where each point can belong to multiple groups with different probabilities.
---

## 📈 Clustering Insights

| **Feature**         | **Cluster 0**         | **Cluster 1**         | **Cluster 2**         |
|---------------------|------------------------|------------------------|------------------------|
| **% of trips**       | 🟩 **76.4%**            | 🟦 **11.7%**            | 🟨 **9.7%**             |
| **passenger_count**  | 1.16                   | 2.48                   | 4.59                   |
| **trip_distance**    | 2.16 mi                | 9.35 mi                | 26.05 mi               |
| **fare_amount**      | \$10.06                | \$31.30                | \$7.75                 |
| **tip_amount**       | \$1.38                 | \$4.86                 | \$1.10                 |
| **total_amount**     | \$12.55                | \$39.75                | \$9.96                 |
| **trip_duration**    | ~11 mins               | ~50 mins               | ~8.7 mins              |
| **pickup_hour**      | 13.7 (≈ 1:40 PM)       | 13.5 (≈ 1:30 PM)       | 14.0 (≈ 2:00 PM)       |

These patterns can support pricing strategies, customer segmentation, or operational planning.

