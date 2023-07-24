# CryptoClustering
Unsupervised Learning Assignment

### Using using Python and Unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.

### Modules used: 
  * Pandas
  * hvplot
  * sklearn
  * StandardScaler()
  * PCA
  * KMeans
  * plotly_express

### Prepare the data:
  * Load the crypto_market_data.csv into a DataFrame.
  * Get the summary statistics and plot the data to see what the data looks like before proceeding.
    ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/3a47c26f-7df5-4026-a814-b0dccf65430e)

  * Use the StandardScaler() module from scikit-learn to normalize the data from the CSV file.
  * Create a DataFrame with the scaled data and set the "coin_id" index from the original DataFrame as the index for the new
    DataFrame.The first five rows of the scaled DataFrame should appear as follows:

    ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/44c34758-04d3-4ba3-acc3-91c007cd32ae)

### Find the Best Value for k Using the Original Scaled DataFrame
  * Used the elbow method to find the best value for k using the following steps:
    * Create a list with the number of k values from 1 to 11.
    * Create an empty list to store the inertia values.
    * Create a for loop to compute the inertia with each possible value of k.
    * Create a dictionary with the data to plot the elbow curve.
    * Plot a line chart with all the inertia values computed with the different values of k to visually identify the 
      optimal value for k.
    * Question: What is the best value for k?
      ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/756b6972-3e36-4dfb-bdc3-1ad334626694)
      
### Cluster Cryptocurrencies with K-means Using the Original Scaled Data 
  * Used the following steps to cluster the cryptocurrencies for the best value for k on the original scaled data:
    * Initialize the K-means model with the best value for k.
    * Fit the K-means model using the original scaled DataFrame.
    * Predict the clusters to group the cryptocurrencies using the original scaled DataFrame.
    * Create a copy of the original data and add a new column with the predicted clusters.
      ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/e792bbb1-41ca-4202-98af-40b61ca53073)

    * Create a scatter plot using hvPlot as follows:
      * Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d".
      * Color the graph points with the labels found using K-means.
      * Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.
      ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/dc8efde3-d22e-4ce4-8863-78b3bcb59a59)

### Optimize Clusters with Principal Component Analysis
  * Using the original scaled DataFrame, perform a PCA and reduce the features to three principal components.
  * Retrieve the explained variance to determine how much information can be attributed to each principal component and
    then answer the following question in your notebook:
    * What is the total explained variance of the three principal components?
      ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/455f745f-c3d6-4a0f-9b83-116cf365d739)

### Find weights per each PCA for the original 7 columns  
  
  ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/70862d6c-545f-4bfc-9b92-970e31835d85)

  ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/58068d10-c81b-44a6-97bc-575f48462006)

  ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/c57cc723-80d6-4645-844e-0f89fbfd14f9)

### Optimizing Clusters with PCA continued...
  * Create a new DataFrame with the PCA data and set the "coin_id" index from the original DataFrame as the index for the
    new DataFrame.The first five rows of the PCA DataFrame should appear as follows:

    ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/ee7d3947-ba4e-4e76-b501-b2f0a943d156)

### Find the Best Value for k Using the PCA Data
  * Used the elbow method on the PCA data to find the best value for k using the following steps:
    * Create a list with the number of k-values from 1 to 11.
    * Create an empty list to store the inertia values.
    * Create a for loop to compute the inertia with each possible value of k.
    * Create a dictionary with the data to plot the Elbow curve.
    * Plot a line chart with all the inertia values computed with the different values of k to visually identify the
      optimal value for k.

      ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/76dd49aa-1d1f-4fb7-a9d8-5663c568cc6c)

### Cluster Cryptocurrencies with K-means Using the PCA Data
  * Used the following steps to cluster the cryptocurrencies for the best value for k on the PCA data:
    * Initialize the K-means model with the best value for k.
    * Fit the K-means model using the PCA data.
    * Predict the clusters to group the cryptocurrencies using the PCA data.
    * Create a copy of the DataFrame with the PCA data and add a new column to store the predicted clusters.
    * Create a scatter plot using hvPlot as follows:
      * Set the x-axis as "PC1" and the y-axis as "PC2".
      * Color the graph points with the labels found using K-means.
      * Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

        ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/c6234c9b-b894-49ce-b5ed-6be76760cd82)

      * Since 3 components - added a 3d perspective plot:

        ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/4fbe7c13-dacc-4b55-9720-bd9154806030)

        ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/0703e705-7c4f-47ae-8e07-46f35563affe)
        

### Visualize and Compare the Results
  * In this section, we visually analyzed the cluster analysis results by contrasting the outcome with and without
    using the optimization techniques.
  * Comparison of plots for elbow method:
    ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/c6ed182d-40c2-44f6-a7bc-200c53379963)

    ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/7e86a4a5-a84d-4b2c-b8e5-169317e7a310)

  * Comparison of scatter plots for clusters original data vs PCA:
    ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/2aa5c39d-a7e7-4884-a1a3-41b8660108b6)

    ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/60c985a2-bd77-434f-8b47-53c9ecdbd9ef)


    ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/128d4275-be7a-4fcb-82e1-1e45c94325c4)


### Cluster Cryptocurrencies with K-means Using the PCA Data, using 3 and 2 number of clusters respectively to verify which
### optimum number gives better precision: 

   ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/2aa736f6-30de-444a-a103-a8356e641c40)
   ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/c373498c-9075-458d-8e8c-182388c78b0d)
   ![image](https://github.com/BijoyetaK/CryptoClustering/assets/126313924/67279ed1-b092-4bb7-a3c2-9e0c1acc67b8)

### references: 
  * Module activities
  * https://plotly.com/python/pca-visualization/
  * https://www.machinelearningplus.com/plots/subplots-python-matplotlib/
  * https://www.geeksforgeeks.org/elbow-method-for-optimal-value-of-k-in-kmeans/
  * https://machinelearningmastery.com/principal-component-analysis-for-visualization/
* https://matplotlib.org/3.1.0/gallery/lines_bars_and_markers/psd_demo.html#sphx-glr-gallery-lines-bars-and-markers-psd-demo-py
    

    



  




    

  





  

  










      


    
    
