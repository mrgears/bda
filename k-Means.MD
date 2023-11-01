### EXP - 8

```
'pip install scikit-learn'
```

```
'# Import necessary libraries
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.datasets import make_blobs


# Generate some sample data
data, _ = make_blobs(n_samples=300, centers=4, random_state=42)


# Initialize the KMeans model with the desired number of clusters (k)
kmeans = KMeans(n_clusters=4)


# Fit the model to your data
kmeans.fit(data)


# Get the cluster labels and cluster centers
labels = kmeans.labels_
centers = kmeans.cluster_centers_


# Visualize the results
plt.figure(figsize=(8, 6))


# Plot the data points with different colors for each cluster
plt.scatter(data[:, 0], data[:, 1], c=labels, cmap='viridis')


# Plot the cluster centers
plt.scatter(centers[:, 0], centers[:, 1], c='red', marker='x', s=200, label='Centers')


plt.title('K-Means Clustering')
plt.xlabel('Feature 1')
plt.ylabel('Feature 2')
plt.legend()
plt.show()
'
```
