# Table of Contents
- [Elbow Method](#elbow-method)
- [K-Means++](#kmeans)
- [Practical Example](#practical-example)
## Elbow Method

**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/34810692#content)**


The **elbow method** is a technique used in clustering (specifically, in **K-means clustering**) to determine the optimal number of clusters in a dataset. The method involves running the clustering algorithm on the dataset for a range of values of \( K \) (the number of clusters) and evaluating a metric called the **inertia** or **within-cluster sum of squares (WCSS)**. 

### Steps for the Elbow Method:
1. **Choose a range of \( K \)**: Decide the range of cluster numbers to test, such as \( K = 1 \) to \( K = 10 \).
2. **Run K-means for each \( K \)**: For each value of \( K \), perform K-means clustering and compute the **inertia**:
$$
\text{Inertia} = \sum_{i=1}^K \sum_{x \in C_i} ||x - \mu_i||^2
$$
 Here:
   - **Cluster ($\ C_i $)**: The $ i $-th cluster.
   - **Data Point ($ x $)**: A data point in cluster $ C_i $.
   - **Centroid ($ \mu_i $)**: The centroid of cluster $ C_i $.



3. **Plot the results**: Plot \( K \) on the x-axis and the corresponding **inertia** on the y-axis.

4. **Find the "elbow"**: Look for a point in the plot where the decrease in inertia sharply levels off. This point represents the optimal \( K \). The rationale is that increasing \( K \) reduces inertia, but after a certain point, the marginal improvement becomes insignificant.

---

### Why is it called the "elbow" method?
The plot of \( K \) versus inertia often resembles an arm, where the **elbow** is the point of inflection that suggests the best trade-off between model complexity (higher \( K \)) and goodness of fit (lower inertia).

### Example Visualization
If you plot \( K \) (1 to 10) versus inertia, the graph might show a steep decline in inertia initially, followed by a flattening curve. The elbow (e.g., \( K = 3 \)) represents the number of clusters where adding more clusters does not significantly reduce inertia.

---

### Limitations of the Elbow Method:
1. The "elbow" might not always be clear, making the choice of \( K \) subjective.
2. It assumes that the data inherently has cluster structure.
3. The method is not robust for non-globular clusters or datasets with varying density.

When the elbow is ambiguous, you may consider additional techniques, like the **Silhouette Score** or the **Gap Statistic**, to validate the choice of \( K \).

---

## KMeans++
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/34978900#content)**

KMeans++ is an improved initialization method for the **KMeans clustering algorithm**. It addresses a common drawback of KMeans: sensitivity to the initial placement of cluster centroids. Poor initialization can lead to suboptimal clusters or increased iterations. KMeans++ ensures better initial centroid placement, leading to faster convergence and better clustering results.

---

### Key Features of KMeans++:
1. **Smart Initialization**: Starts with centroids that are farther apart, reducing the likelihood of poor clustering.
2. **Efficiency**: Adds only a small computational overhead compared to random initialization.
3. **Improved Results**: Often achieves lower inertia (better clustering quality).

---

### How KMeans++ Works:

1. **Choose the First Centroid Randomly**:
   - Select one data point randomly as the first centroid.

2. **Calculate Distances**:
   - For each remaining data point, calculate its squared distance to the nearest chosen centroid.

3. **Probability-Based Selection**:
   - Choose the next centroid probabilistically. Points farther away from existing centroids are more likely to be chosen.
   - The probability of selecting a point \( x \) is proportional to \( D(x)^2 \), where \( D(x) \) is the distance of \( x \) to its nearest centroid.

4. **Repeat Until \( K \) Centroids Are Chosen**:
   - Continue steps 2 and 3 until \( K \) centroids are initialized.

5. **Proceed with Standard KMeans**:
   - Use these initialized centroids as the starting point for the KMeans clustering algorithm.

---

### Why KMeans++ is Better:
1. **Avoids Poor Initialization**:
   - Random initialization can lead to centroids being clustered together or poorly positioned.
   - KMeans++ ensures centroids are well-separated initially, improving the chances of finding good clusters.

2. **Faster Convergence**:
   - Better initial centroids reduce the number of iterations required to converge.

3. **Higher Accuracy**:
   - Leads to lower within-cluster sum of squares (WCSS), improving clustering performance.

---

### Pseudocode for KMeans++:

1. Choose the first centroid randomly from the dataset.
2. For each data point, calculate the distance to the nearest chosen centroid.
3. Compute probabilities for each point based on their squared distances.
4. Select the next centroid based on these probabilities.
5. Repeat until \( K \) centroids are initialized.
6. Run standard KMeans clustering.

---

### Example:
Suppose you want 3 clusters (\( K = 3 \)) in a dataset:
1. Randomly pick one data point as the first centroid.
2. Compute the squared distance of all other points to this centroid.
3. Select the second centroid with a probability proportional to the squared distance.
4. Repeat for the third centroid.
5. Run KMeans using these initialized centroids.

---

### Advantages:
- Reduces chances of poor clustering.
- Simple to implement and computationally efficient.
- Particularly effective for datasets with varying densities or complex shapes.

KMeans++ is now the default initialization method in most modern libraries (e.g., `scikit-learn`).


# Practical Example
See the practical example in the video and the practical notebook in the practical folder.  
**Watch the video: [▶️](https://www.udemy.com/course/machinelearning/learn/lecture/19509906#content)**