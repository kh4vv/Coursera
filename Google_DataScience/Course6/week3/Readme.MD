# Glossary terms from week 3

### Terms and definitions from Course 6, Week 3

**Affinity:** The metric used to calculate the distance between points/clusters

**Agglomerative clustering:** A clustering methodology that works by first assigning every point to its own cluster, then progressively combining clusters based on intercluster distance

**Average:** The distance between each cluster’s centroid and other clusters’ centroids

**Centroid:** The center of a cluster determined by the mathematical mean of all the points in that cluster

**Complete:** The maximum pairwise distance between clusters

**DBSCAN:** A clustering methodology that searches data space for continuous regions of high density; stands for “density-based spatial clustering of applications with noise” 

**distance_threshold:** A hyperparameter in agglomerative clustering models that determines the distance above which clusters will not be merged 

**eps (Epsilon):** In DBSCAN clustering models, a hyperparameter that determines the radius of a search area from any given point

**Inertia:** The sum of the squared distances between each observation and its nearest centroid	 

**K-means:** An unsupervised partitioning algorithm used to organize unlabeled data into groups, or clusters

**K-means++:** An optimization of K-means that chooses the first centroid uniformly at random from the data points, after which each subsequent centroid is chosen from the remaining points with probability proportional to its squared distance from the point's closest existing centroid

**Linkage:** The method used to determine which points/clusters to merge

**min_samples:** In DBSCAN clustering models, a hyperparameter that specifies the number of samples in an ε-neighborhood for a point to be considered a core point (including itself)

**n_clusters:** In K-means and agglomerative clustering models, a hyperparameter that specifies the number of clusters in the final model

**Silhouette analysis:** The comparison of different models’ silhouette scores

**Silhouette score:** The mean of the silhouette coefficients of all the observations in a model

**Single:** The minimum pairwise distance between clusters

**Ward:** Merges two clusters whose merging will result in the lowest inertia
