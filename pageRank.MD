### EXP-9

```
'import numpy as np

def pagerank(adj_matrix, d=0.85, max_iter=100, tol=1e-6):
    n = len(adj_matrix)
    pr = np.ones(n) / n

    for i in range(max_iter):
        pr_new = np.zeros(n)
        for j in range(n):
            for k in range(n):
                if adj_matrix[k][j] == 1:
                    pr_new[j] += pr[k] / np.sum(adj_matrix[k])
        pr_new = (1 - d) / n + d * pr_new

        if np.sum(np.abs(pr_new - pr)) < tol:
            return pr_new

        pr = pr_new

    return pr
# Example adjacency matrix (0-based indexing)
adj_matrix = np.array([
    [0, 1, 1],
    [1, 0, 0],
    [1, 1, 0]
])

# Calculate PageRank
pagerank_values = pagerank(adj_matrix)
print("PageRank values:", pagerank_values)
'
```
