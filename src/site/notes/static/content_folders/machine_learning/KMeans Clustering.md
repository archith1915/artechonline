---
{"dg-publish":true,"permalink":"/static/content-folders/machine-learning/k-means-clustering/","dgShowToc":true}
---

# What is K-Means?

K-Means is an unsupervised machine learning algorithm used for clustering data into groups based on similarity. It works by dividing a dataset into a predefined number of clusters (K), where each cluster contains data points that are more similar to each other than to those in other clusters. The "means" in K-Means refers to the average position (centroid) of the data points in a cluster, which the algorithm tries to optimize during training.


# What Does K-Means Do?

K-Means aims to group data points in such a way that the variation within each cluster is minimized and the variation between clusters is maximized. It does this by calculating the centroids of clusters and then assigning each data point to the nearest centroid. The process is repeated iteratively until the clusters become stable. In essence, it organizes data into natural groupings based on feature similarities.


# How Does K-Means Work?

The K-Means algorithm begins by selecting K random points as the initial cluster centroids. Each data point is then assigned to the cluster whose centroid is closest to it. Once all points are assigned, the centroids are recalculated as the average of all the points in each cluster. These steps—assignment and centroid update—are repeated until the centroids no longer change significantly or until a maximum number of iterations is reached. This iterative refinement leads to stable clusters.


# Why Use K-Means?

K-Means is favored for its simplicity, speed, and scalability. It works well with large datasets and provides easily interpretable results, especially when the data is numeric and continuous. It is a go-to method for quick clustering tasks when you need to discover patterns, group similar data, or reduce data complexity. Its computational efficiency makes it useful in real-time and big data applications.

# When to Use K-Means?

You should use K-Means when your goal is to find natural groupings within a dataset, such as identifying customer segments or patterns in unlabeled data. It is most effective when the data forms well-separated, spherical clusters and when you have a rough estimate of how many clusters (K) you want. K-Means performs best when the dataset has uniform feature scales and relatively balanced cluster sizes.

# Common Use Cases

K-Means is used in a variety of fields and applications. In marketing, it helps segment customers based on purchasing behavior. In computer vision, it assists with image compression by grouping similar pixel colors. In document analysis, it can cluster articles or reviews by topic. It is also used in anomaly detection to identify data points that don’t fit well in any cluster, indicating outliers or unusual behavior.



# Limitations of K-Means

Despite its advantages, K-Means has several limitations. It requires the number of clusters (K) to be defined in advance, which may not always be known. The algorithm is sensitive to the initial placement of centroids, which can affect the final clusters, sometimes leading to suboptimal solutions. It also assumes clusters are spherical and equally sized, making it unsuitable for more complex cluster shapes. Additionally, K-Means is affected by outliers, which can distort cluster centroids.


# Mathematics Behind K-Means

The K-Means algorithm minimizes an objective function known as the **within-cluster sum of squares** (WCSS). Mathematically, it seeks to minimize the total squared distance between each data point and the centroid of the cluster to which it belongs. This optimization ensures that data points are as close as possible to the center of their cluster, resulting in compact, well-defined groupings.

# Summary

|Aspect|Description|
|---|---|
|Algorithm type|Unsupervised clustering algorithm|
|Model assumption|Clusters are spherical and equally sized|
|Key parameters|Number of clusters (K), initial centroid positions|
|Strengths|Simple, fast, scalable, works well with large numeric data|
|Weaknesses|Requires predefined K, sensitive to initialization, affected by outliers, assumes spherical clusters|
|Output|Cluster assignments and cluster centroids|


# Code

```python
from sklearn.datasets import load_iris

from sklearn.mixture import GaussianMixture

from sklearn.cluster import KMeans

from sklearn.metrics import silhouette_score

import matplotlib.pyplot as plt

  

X = load_iris().data

kmeans = KMeans(n_clusters = 3, random_state = 42).fit(X)

gmm = GaussianMixture(n_components=3, random_state = 42).fit(X)

k_labels, g_labels = kmeans.predict(X), gmm.predict(X)

print(f"Silhouette score for KMeans : {silhouette_score(X, k_labels):.2f} - Silhouette Score for GMM : {silhouette_score(X, g_labels):.2f}")

  

plt.subplot(1,2,1); plt.scatter(X[:,0], X[:,1], c=k_labels); plt.title("k-Means")

plt.subplot(1,2,2); plt.scatter(X[:,0], X[:,1], c=g_labels); plt.title("GMM (EM)"); plt.show()
```


# Explanation


This code compares two clustering algorithms—K-Means and Gaussian Mixture Model (GMM)—on the Iris dataset, and evaluates them using the Silhouette Score, a measure of cluster quality.


## Step-by-Step Explanation

### 1. Importing Necessary Libraries

```python
from sklearn.datasets import load_iris
from sklearn.mixture import GaussianMixture
from sklearn.cluster import KMeans
from sklearn.metrics import silhouette_score
import matplotlib.pyplot as plt
```

- What: Imports datasets, clustering algorithms (KMeans, GMM), silhouette scoring, and plotting tools.  
- Why: These libraries provide ready-to-use clustering models and evaluation metrics.

---

### 2. Loading the Iris Dataset


```python
X = load_iris().data
```

- What: Loads the input features (X) from the classic Iris dataset (4D feature space).  
- Why: Iris is a well-known benchmark for clustering; it has 3 natural classes, ideal for demonstrating clustering behavior.

---

### 3. Applying K-Means Clustering

```python
kmeans = KMeans(n_clusters=3, random_state=42).fit(X)
```

- What: Applies K-Means with 3 clusters and a fixed seed for reproducibility.  
- Why: Clusters the data into 3 groups, as expected from the original dataset.

---

### 4. Applying Gaussian Mixture Model (GMM) Clustering

```python
gmm = GaussianMixture(n_components=3, random_state=42).fit(X)
```

- What: Applies GMM with 3 components.  
- Why: GMM uses probabilistic clustering (soft clustering) and is more flexible than K-Means (e.g., can model elliptical clusters).

---

### 5. Predicting Cluster Labels

```python
k_labels, g_labels = kmeans.predict(X), gmm.predict(X)
```

- What: Predicts cluster assignments for each sample using both models.  
- Why: You need the labels to evaluate and visualize how well the data has been clustered.

---

### 6. Calculating Silhouette Scores

```python
print(f"Silhouette score for KMeans : {silhouette_score(X, k_labels):.2f} - Silhouette Score for GMM : {silhouette_score(X, g_labels):.2f}")
```

- What: Computes the silhouette score for each clustering result.  
- Why: Measures how similar an object is to its own cluster vs others. Higher = better clustering (ranges from -1 to 1).

---

### 7. Plotting the Clusters

```python
plt.subplot(1,2,1); plt.scatter(X[:,0], X[:,1], c=k_labels); plt.title("k-Means")
plt.subplot(1,2,2); plt.scatter(X[:,0], X[:,1], c=g_labels); plt.title("GMM (EM)")
plt.show()
```

- What: Plots the clusters formed by both algorithms using the first two features of the dataset.  
- Why: Visual comparison helps understand how each algorithm separates data. It’s easier to judge cluster shape, overlap, and separation.

---

## Why This Should Be Done

- Algorithm Comparison: Helps evaluate which clustering method is better for a given dataset.
- Evaluation with Silhouette Score: Quantifies the performance instead of just relying on visual intuition.
- Model Selection: Useful in real-world applications to choose the most suitable clustering algorithm.
- Understanding Strengths/Weaknesses:
  - K-Means is fast but assumes spherical clusters.
  - GMM is more flexible but computationally heavier.
- Educational Value: Great for learning the difference between hard and soft clustering methods.
