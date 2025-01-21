# Table of Contents
- [Hierarchical Clustering](#hierarchical-clustering)
  - [Types of Hierarchical Clustering](#types-of-hierarchical-clustering)
- [Practical Example](#practical-example)

## Hierarchical Clustering
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/5714428#content)**

Hierarchical clustering is a method of clustering that builds a hierarchy of clusters. It is widely used when the number of clusters (\( K \)) is unknown and when understanding the nested relationships among data points is important.

---

### Types of Hierarchical Clustering
1. **Agglomerative (Bottom-Up)**:
   - Starts with each data point as a separate cluster.
   - Iteratively merges the closest clusters until all points form a single cluster or a stopping criterion is met.
   - Most commonly used.

2. **Divisive (Top-Down)**:
   - Starts with all data points in one single cluster.
   - Iteratively splits the cluster into smaller clusters until each data point is its own cluster or a stopping criterion is met.
   - Less commonly used due to higher computational cost.

---
### Steps in Agglomerative Clustering

1. **Start with Individual Clusters**:
   - Each data point is treated as its own cluster.

2. **Compute Distances**:
   - Calculate pairwise distances (or similarity) between all clusters using a distance metric (e.g., Euclidean, Manhattan, Cosine).

3. **Merge Closest Clusters**:
   - Identify the two clusters that are closest to each other and merge them.

4. **Update Distances**:
   - After merging, recalculate the distances between the new cluster and the remaining clusters.

5. **Repeat**:
   - Continue merging until one cluster contains all data points or a specific number of clusters is reached.

---

### Steps in Divisive Clustering (Top-Down)

1. **Start with All Data in One Cluster**:
   - Treat the entire dataset as a single cluster.

2. **Split the Cluster**:
   - Divide the cluster into two smaller clusters using a method like K-means (\( K = 2 \)) or by maximizing dissimilarity.

3. **Recompute Dissimilarities**:
   - Update distances or similarities between the new clusters and data points.

4. **Repeat Splitting**:
   - Continue splitting the largest or most heterogeneous cluster until each data point is its own cluster or a stopping criterion is met.

5. **Visualize with a Dendrogram**:
   - Build a dendrogram to show the hierarchy of splits.

---

### Linkage Criteria
The way distances between clusters are calculated depends on the linkage criteria. Common linkage methods include:

1. **Single Linkage**:
   - Distance between two clusters is the shortest distance between any two points in the clusters.
   - Tends to produce long, "chain-like" clusters.

2. **Complete Linkage**:
   - Distance between two clusters is the longest distance between any two points in the clusters.
   - Produces more compact clusters.

3. **Average Linkage**:
   - Distance between two clusters is the average of all pairwise distances between points in the clusters.

4. **Centroid Linkage**:
   - Distance between two clusters is the distance between their centroids.

---

### Visualizing Hierarchical Clustering
The results of hierarchical clustering can be visualized using a **dendrogram**, which is a tree-like diagram that shows the sequence of merges:

- **X-axis**: Data points or clusters.
- **Y-axis**: Distance or similarity at which clusters are merged.

#### How to Use a Dendrogram:
- Cut the dendrogram at a certain height to determine the number of clusters.
- The height represents the distance or dissimilarity between clusters.

---

### Advantages of Hierarchical Clustering:
1. **No Need to Predefine \( K \)**:
   - Unlike K-means, it doesn’t require specifying the number of clusters in advance.
2. **Captures Nested Structures**:
   - Shows how clusters are related at different levels of granularity.
3. **Works with Small Datasets**:
   - Particularly useful for small datasets where hierarchical relationships matter.

---

### Disadvantages:
1. **Computationally Expensive**:
   - Time complexity is \( O(n^2 \log n) \), making it impractical for very large datasets.
2. **Sensitive to Noise and Outliers**:
   - Can lead to distorted clusters.
3. **Irreversible**:
   - Once a merge or split is done, it cannot be undone.

---

### Applications:
- **Bioinformatics**: Gene sequencing and protein analysis.
- **Marketing**: Customer segmentation.
- **Natural Language Processing (NLP)**: Document clustering.
- **Social Sciences**: Analyzing survey or experimental data.

---

### Tools and Libraries:
- **Python Libraries**:
  - `scipy.cluster.hierarchy` for creating dendrograms.
  - `sklearn.cluster.AgglomerativeClustering` for practical implementation.

# Practical Example
See the practical example in the video and the practical notebook **[here](./practical/hierarchical_clustering.ipynb)**.  
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/19534146#content)**

