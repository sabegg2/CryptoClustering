# CryptoClustering
- Module 19 Challenge
- Steph Abegg

In this challenge, we used our knowledge of Python and unsupervised learning with k-means clustering to create a machine learning model that groups cryptocurrencies and predicts if cryptocurrencies are affected by 24-hour or 7-day price changes.

My code for this be found in [Crypto_Clustering.ipynb](Crypto_Clustering.ipynb)

## Steps

1. I used the `StandardScaler()` module from `scikit-learn` to normalize the data.

2. Using the scaled data, I created an elbow plot to find the best value of `k`. From the elbow plot, the best value for `k` is 4.
   
3. I then fit the scaled data with a k-means model with 4 clusters, in order to cluster the different crypto currencies into 4 groups. I plotted the groups in a scatter plot.

4. I then used Principal Component Analysis (PCA) to reduce the features of the scaled dataframe down to 3. The explained variance of these three features was 89.5%.

5. Now using the PCA data, I repeated the process of creating an elbow plot to find the best value of `k`. Again, the best value for `k` appears to be 4. 

6. Also, again now using the PCA data, I repeated the process of fitting the data with a k-means model with 4 clusters.
   
7. Finally, I compared the the elbow curves and the scatter plots before and after PCA. Images are shown below.

## Plots

<img src="images/elbow_plots.png" width=700>
<img src="images/cluster_plots.png" width=700>

## Conclusions

For both the original data and the PCA data with three components, the best value of `k` is 4. This suggests that a PCA model with three features is appropriate for this data set.

Using fewer features in the PCA model to cluster the data causes the clusters to become more concentrated compared to the original data. Also, in the PCA plot, cluster 3 (`coin_id` = "celsius-degree-token") is distanced from clusters 0 and 2 (each with sevearl different contributing `coin_id`) which is in contrast to the original data plot where cluster 3 appears to be amongst cluster 0. This indicates that there is a primary feature in the original data which is causing coin_id "celsius_degree_token" to have its own cluster. 
