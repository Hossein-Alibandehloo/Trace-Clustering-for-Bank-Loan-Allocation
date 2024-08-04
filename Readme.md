# Trace Clustering for Bank Loan Allocation

## Introduction
To evaluate and categorize existing processes in the loan allocation procedure, we employed three clustering algorithms: K-Means, K-Modes, and Hierarchical Clustering. We utilized the Silhouette index as an evaluation metric for clustering quality across all methods. Additionally, for Hierarchical Clustering, the Cophenetic Correlation Coefficient (CPCC) was used to select the best merging method. The results indicated that all three methods identified 7 clusters as the optimal number, with a Silhouette score of 0.98.

## 1. K-Means Algorithm
In this dataset, we have 49 loan allocation cases. Initially, each trace for these cases was represented as a sequence of activities. We then calculated the distance matrix using the Levenshtein method. The K-Means algorithm was applied to this distance matrix, and we evaluated the results of each cluster using the Silhouette index. The optimal number of clusters was found to be 7.

![Silhouette_Score_for_Different_k_Kmeans](Charts\Kmeans\Silhouette_Score_for_Different_k.png)

## 2. K-Modes Algorithm
Similar to K-Means, the K-Modes algorithm also determined 7 as the optimal number of clusters, with an average Silhouette score of 0.98.

![Silhouette_Score_for_Different_k_KModes](Charts\Kmodes\Silhouette_Score_for_Different_k_kmodes.png)

## 3. Agglomerative Hierarchical Clustering
We performed hierarchical clustering using various methods. The method with the highest CPCC, indicating the best approach for merging similar clusters, was the 'average' method.

![Silhouette_Score_for_Different_k_Hierarchical_Clustering](Charts\Hierarchical_Clustering\Silhouette_Score_for_Different_k_hierarchical_clustering.png)

### CPCC by Method
| Method   | CPCC  |
|----------|-------|
| Single   | 0.847 |
| Complete | 0.944 |
| Average  | 0.956 |
| Centroid | 0.953 |
| Median   | 0.953 |
| Weighted | 0.947 |
| Ward     | 0.833 |

Using the 'average' method, we identified 7 clusters as the optimal number, consistent with the other algorithms.

## 4. Cluster Interpretation
The following table summarizes the distribution and characteristics of each cluster:

| Cluster | Cases | % of Total (Cumulative) | Avg. Completion Time | Avg. Number of Activities |
|---------|-------|-------------------------|----------------------|---------------------------|
| 5       | 22    | 45%                     | 0 days 00:00:44.62   | 2                         |
| 3       | 11    | 67%                     | 0 days 00:00:33.98   | 6                         |
| 7       | 9     | 86%                     | 1 days 14:54:55.93   | 6                         |
| 6       | 2     | 90%                     | 167 days 01:30:20.99 | 8                         |
| 1       | 2     | 94%                     | 3 days 23:39:35.06   | 12                        |
| 4       | 2     | 98%                     | 0 days 00:02:26.96   | 2                         |
| 2       | 1     | 100%                    | 0 days 02:02:45.60   | 16                        |

### Key Observations
- **Clusters 5, 3, and 7**: These clusters contain approximately 86% of all loan allocation cases, with clusters 5 and 3 showing particularly quick completion times.
- **Cluster 6**: Although it includes only 2 cases, the average process time was significantly longer at 167 days, with a notably high number of activities.
- **Clusters 1, 4, and 2**: These clusters consist of fewer cases, with a distinct set of characteristics that warrant further investigation.

### Detailed Cluster Analysis
#### Cluster 5
This cluster consists of two activities: the payment information activity took approximately 15 seconds on average, followed by a collective loan payment to 22 cases. This unusual pattern suggests potential anomalies, possibly indicating fraudulent behavior.

<div style="display: flex; justify-content: space-between;">
  <div style="margin-right: 5px;">
    <img src="Charts\Clusters\5_1.png" width="45%">
  </div>
  <div>
    <img src="Charts\Clusters\5_2.png" width="45%">
  </div>
</div>

#### Cluster 3
In Cluster 3, activities were evenly distributed across the 11 cases. The first activity, 'Selection and Review for Loan Payment,' took the longest time compared to other activities.

<div style="display: flex; justify-content: space-between;">
  <div style="margin-right: 5px;">
    <img src="Charts\Clusters\3_1.png" width="100%">
  </div>
  <div>
    <img src="Charts\Clusters\3_2.png" width="100%">
  </div>
</div>

#### Cluster 7
In this cluster, the 'Review and Feedback' activity was repeated almost twice as much as other activities, likely due to issues with incomplete documentation, resulting in significant delays.

<div style="display: flex; justify-content: space-between;">
  <div style="margin-right: 5px;">
    <img src="Charts\Clusters\7_1.png" width="100%">
  </div>
  <div>
    <img src="Charts\Clusters\7_2.png" width="100%">
  </div>
</div>

#### Cluster 6
With an average process time of 167 days, this cluster included only 2 cases. All activities were conducted in quick succession, except for the notification of payment, which occurred much later.

<div style="display: flex; justify-content: space-between;">
  <div style="margin-right: 5px;">
    <img src="Charts\Clusters\6_1.png" width="100%">
  </div>
  <div>
    <img src="Charts\Clusters\6_2.png" width="100%">
  </div>
</div>

#### Cluster 1
This cluster featured the most extended time spent on the payment notification activity, with an average of 12 activities per process. Each case in this cluster took around 3 days to complete.

<div style="display: flex; justify-content: space-between;">
  <div style="margin-right: 5px;">
    <img src="Charts\Clusters\1_1.png" width="100%">
  </div>
  <div>
    <img src="Charts\Clusters\1_2.png" width="100%">
  </div>
</div>

#### Cluster 4
Similar to Cluster 5, this cluster had only two activities and two cases. The activities in this cluster are not clearly interpretable, and further analysis is needed to determine if these cases are outliers.

<div style="display: flex; justify-content: space-between;">
  <div style="margin-right: 5px;">
    <img src="Charts\Clusters\4_1.png" width="100%">
  </div>
  <div>
    <img src="Charts\Clusters\4_2.png" width="100%">
  </div>
</div>

#### Cluster 2
This cluster, containing only one case, involved 16 distinct activities, most of which occurred before the review and feedback stage. Surprisingly, all these activities were completed within approximately 2 hours, raising questions about the process's normalcy.

<div style="display: flex; justify-content: space-between;">
  <div style="margin-right: 5px;">
    <img src="Charts\Clusters\2_1.png" width="100%">
  </div>
  <div>
    <img src="Charts\Clusters\2_2.png" width="100%">
  </div>
</div>

## Conclusion
The clustering analysis revealed significant insights into the loan allocation process, identifying both typical patterns and anomalies. Further investigation is needed to understand the outlier cases fully and ensure the integrity of the loan allocation process.
