# Video Script: Part 1 - K-Means Clustering: From Zero to Hero
**Author:** Weihao Fu

---

Hello everyone, I'm Weihao Fu. In this video, I'll walk you through K-Means clustering, from the basic algorithm to real-world applications.

**[0:00 - 1:00] Introduction**

K-Means is a prototype-based clustering algorithm. The idea is simple: we want to partition data into K clusters, where each cluster is represented by its centroid - the mean of all points in that cluster.

The algorithm works in two steps that repeat until convergence:
1. Assignment: assign each point to the nearest centroid
2. Update: recompute each centroid as the mean of its assigned points

**[1:00 - 3:00] The Basics**

Let's start with synthetic data. I'll generate blobs using sklearn's make_blobs, then run KMeans with different K values. Notice how the algorithm finds the natural groupings.

Key parameters:
- `n_clusters`: the K we choose
- `n_init`: number of random initializations (we use 10 to avoid bad local minima)
- `random_state`: for reproducibility

**[3:00 - 5:00] Choosing K**

How do we pick K? Two popular methods:

1. Elbow method: plot inertia (within-cluster sum of squares) vs K. Look for the "elbow" where adding more clusters gives diminishing returns.

2. Silhouette score: measures how similar each point is to its own cluster vs other clusters. Ranges from -1 to 1; higher is better.

I'll demonstrate both on the iris dataset.

**[5:00 - 7:00] Real Data: Text Clustering**

Now let's cluster text documents. I'll use TF-IDF to convert documents to vectors, then apply TruncatedSVD (also called LSA) to reduce to 100 dimensions. This makes K-Means run fast on dense vectors.

We compare two representations:
- TF-IDF + LSA: classic bag-of-words approach
- Sentence embeddings: using a transformer model for semantic similarity

We evaluate with ARI (Adjusted Rand Index) and NMI (Normalized Mutual Information) against the true categories.

**[7:00 - 8:00] Image Clustering**

For images, I'll extract features using a pretrained ResNet-18, then cluster in that feature space. This shows how K-Means works on top of deep learning representations.

**[8:00 - 9:00] Conclusion**

K-Means is simple but powerful. Key takeaways:
- Always scale your features (StandardScaler)
- Use n_init=10 to avoid bad local minima
- Choose K with elbow method or silhouette score
- For high-dimensional data like text, reduce dimensions first

Thanks for watching!
