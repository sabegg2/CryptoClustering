# CryptoClustering
- Module 19 Challenge
- Steph Abegg

In this challenge, you'll use your knowledge of Python and unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.

For this module’s Challenge, you will create a machine learning model that groups cryptocurrencies. The purpose will be to assemble investment portfolios that are based on the profitability of those cryptocurrencies.


This challenge demonstrates the usage of unsupervised learning with k-means clustering.

Using the provided data on Crypto Currencies, containing 7 features, I explored clustering the data. The analysis, plots, and code can be found in Crypto_Clustering.ipynb

## Steps

1. I used the `StandardScaler()` module from `scikit-learn` to normalize the data.

2. Using the scaled data, I created an elbow plot to find the best value of `k`. From the elbow plot, the best value for `k` is 4.
   
3. I then fit the scaled data with a k-means model with 4 clusters, in order to cluster the different crypto currencies into 4 groups. I plotted the groups in a scatter plot.

4. I then used Principal Component Analysis (PCA) to reduce the features of the scaled dataframe down to 3. The explained variance of these three features was 89.5%.

5. I repeated the process of creating an elbow plot to find the best value of `k` for the PCA data. Again, the best value for `k` appears to be 4.

6. I repeated the process of fitting the data (this time the PCA data) with a k-means model with 4 clusters.

using the elbow method and fitting the PCA data with a k-means model.
   
Using PCA and the elbow method, the best value of k was again determined to be 4, leading to the conclusion that PCA with 3 features was appropriate for this data set.
Finally, I compared the the elbow curves and the scatter plots before and after PCA. Images are shown below.
Overall, using PCA made the outliers more obvious, however, it does not make clusters 0 and 3 appear more distinct, at least with the two dimensions shown.

 Using fewer features to cluster the data causes the majority clusters to become much more concentrated compared to the original data plot. The PCA plot, with fewer features, has also distanced cluster 3 (coin_id = "celsius-degree-token") from clusters 0 and 2 which is in contrast to the original data plot where cluster 3 appears to be amongst cluster 0. This clearly shows that there is a feature within the original data which is having a strong contribution to coin_id "celsius_degree_token" to have it's own cluster; which is not coming through on the plot. The PCA data, in my opinion, displays a much better representation of the clusters, and that 4 is in fact the correct number of clusters required for this dataset.

  Fewer features might not show all the important information from the data, and may lead a less defined separation between clusters. In the PCA data plot, where we used more features, we can see that the clusters are very distinct and don't overlap, while in the original data plot there was overlap.

  Using fewer features did not affect the number of clusters (k) as show with the plot of the elbow curves. In the plot of the clusters, it is much more clear that groups 1 and 2 are very distinct from the rest of the crypto coins while clusters 0 and 3 seem to be very similar.

## Plots

<img src="images/elbow_plots.png" width=700>
<img src="images/cluster_plots.png" width=700>
