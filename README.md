# CryptoClustering
- Module 19 Challenge
- Steph Abegg

In this challenge, we used our knowledge of Python and unsupervised learning with k-means clustering to create a machine learning model that groups cryptocurrencies and predicts if cryptocurrencies are affected by 24-hour or 7-day price changes.

My code for this be found in [Crypto_Clustering.ipynb](Crypto_Clustering.ipynb)

## Steps

1. I used the `StandardScaler()` module from `scikit-learn` to normalize the data.

2. Using the scaled data, I performed a cluster analysis with K-means. K-Means is a classical clustering algorithm that partitions data into a predefined number of clusters based on similarity (usually measured by Euclidean distance). It tries to minimize the variance within each cluster. The K-Means cluster analysis entailed:
   - Using a for loop to determine the inertia for each k between 1 through 10.
   - Creating an elbow plot of inertia against the number of clusters.
   - Determining where the "elbow" of the plot is, and at which value of k it appears (k=4).
What exactly does the "elbow" mean? The inertia measures how tightly grouped the data points are within a cluster. The "elbow" point is where the inertia starts diminishing at a slower rate. This indicates that adding more clusters beyond this point doesn't provide much better modeling of the data. The "elbow" in the elbow plot below appears to be at k=4. This is the optimal number of clusters. This point suggests that adding more clusters beyond 3 clusters provides diminishing returns in explaining variance or reducing error.

3. I then fit the scaled data with a k-means model with 4 clusters, in order to cluster the different crypto currencies into 4 groups. I plotted the groups in a scatter plot, setting `x="price_change_percentage_24h"` and `y="price_change_percentage_7d"`.

4. I then used Principal Component Analysis (PCA) to reduce the features of the scaled dataframe down to 3. The explained variance of these three features was 89.5%. (Dimensionality reduction with PCA is a statistical technique used to reduce the number of dimensions (features) in a dataset while retaining most of the variation or information present in the original data. The goal is to simplify the dataset, making it easier to visualize or analyze, without losing too much important information. Preserving 89.5% of the variance, the number of features was reduced from 7 to 3).

5. Now using the PCA data, I repeated the process of creating an elbow plot to find the best value of `k`. Again, the best value for `k` appears to be 4. 

6. Also, again now using the PCA data, I repeated the process of fitting the data with a k-means model with 4 clusters. I plotted the groups in a scatter plot with the Principal Components PC1 and PC2 as the axes. PC1 and PC2 capture the most variance (spread) in the data, so plotting them helps visualize the overall structure of the data in 2D. The plot shows how well the K-Means clustering has separated the data based on the first two principal components. There are four distinct clusters. 
   
7. Finally, I compared the the elbow curves and the scatter plots before and after PCA. Images are shown below.

## Plots

<img src="images/elbow_plots.png" width=700>
<img src="images/cluster_plots.png" width=700>

## Conclusions

For both the original data and the PCA data with three components, the best value of `k` is 4. This suggests that a PCA model with three features is appropriate for this data set.

Using fewer features in the PCA model to cluster the data causes the clusters to become more concentrated compared to the original data. Also, in the PCA plot, cluster 3 (`coin_id` = "celsius-degree-token") is distanced from clusters 0 and 2 (each with sevearl different contributing `coin_id`) which is in contrast to the original data plot where cluster 3 appears to be amongst cluster 0. This indicates that there is a primary feature in the original data which is causing coin_id "celsius_degree_token" to have its own cluster. It is worth noting that while clusters 0 and 2 both encompass several different `coin_id`, clusters 1 and 3 both have just one `coin_id` ("ethlend" for cluster 0 and "celsius-degree-token" for cluster 3).
