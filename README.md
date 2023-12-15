# Partitioning-Clustering---Vehicle-Data-Set---with-R
There are 846 observations or features captured from various angels. The observations include 19 numerical features that was taken for object recognition purposes. The purpose of this data set is to classify the silhouette of a given vehicle. Based on the description provided, the data set is used to perform k-means clustering.

Partitioning Clustering
Introduction
The vehicle data set consists of details silhouettes of four different types of vehicles. Which are the following types that the vehicle data set consists of.
1.	Van
2.	Saab
3.	Bus
4.	Opel
There are 846 observations or features captured from various angels. The observations include 19 numerical features that was taken for object recognition purposes. The purpose of this data set is to classify the silhouette of a given vehicle. Based on the description provided, the data set is used to perform k-means clustering and identify the ideal number of clusters based on the given data set. 
2.1 Ideal Number of Clusters
The vehicle data set consist of 20 attributes in total and the first attribute “Samples” is not required for the k-means. Therefore, the column is dropped from the data frame. 
Based on the given data set, under the “Class” attribute for each observation the respective class is mentioned. Prior to k-means clustering, it is important to identify from the given data set what instance belongs to which class (Appendix 2.1.1). 
Bus
	Opel	Saab	Van
218	212	217	199

Thereafter, based on the above table, the observations are broken accordingly and clustered (Appendix 2.1.2). 
 
Figure 1 Cluster Plot (4 Clusters)
The above cluster plots represent all the observations based on the original vehicle data frame. This is to interpret how the clusters are visualized. Based on the above cluster plot, the clusters have many overlaps among the clusters. 
Based on the above cluster plot it is evident that some observations maybe outliers and may need to be removed. For instance, under cluster group 4 the instance number 5 may affect the outcome of the clusters. 
2.2 Removing Outliers
For deriving an accurate clustering result, the outliers require to be removed. To remove these outliers, by using z-score method, calculating the z-score for each attribute. Thereafter, setting a threshold value greater than 3 and remove observations that does not belong to the criteria. Prior to using z-score method to remove the outliers. There were 846 observations and after applying z-score, the observations reduced to 824. This will remove any outliers and help improve the clustering (Appendix 2.2.1). 
To perform clustering the data set needs to be scaled. Since, clustering measure distance between data points and determine if they are similar or not. Therefore, the data needs to be scaled to get an accurate clustering result and analysis (Appendix 2.2.2).
Based on the above preprocessing, visualizing the 4 main clusters by using the preprocessed data (Appendix 2.2.3). 
 
Figure 2 Cluster Plot (Preprocessed Data)
Based on the cluster plot above, after preprocessing which involved removing outliers and scaling the dataset, four clusters were generated based on the given data set. Visually, it is possible to distinguish the four clusters. However, some overlaps are still visible.
2.3 Identifying Ideal Number of Clusters
Based on the data set it is important to identify the number clusters based on the preprocessed data set. To derive the optimal number of clusters, elbow method is used to determine the best cluster numbers.
The elbow method uses to plot the within-cluster sum of squares also known as WSS against the number of clusters. The "elbow" point in the graph below represents the number of clusters along the x axis. As the number of clusters increase, the WSS decreases. In the plot below, we can see that there is a visible elbow point at two clusters, indicating that the first cluster count is two. However, there is another visible elbow point at three clusters. After the fourth cluster, the WSS becomes a flat line. Based on the elbow method, it is visually evident that the ideal number of clusters for this dataset is two or three (Appendix 2.3.1).
 
Figure 3 Elbow Method Graph
Therefore, it is difficult to determine the optimum number of clusters using elbow method based on the above graph. Therefore, in relation to identifying number of clusters another method is used named Silhouette method. This method calculates the average silhouette width for each cluster and the overall score (Appendix 2.3.2). 
 
Figure 4 Silhouette Method Graph
Based on the silhouette method graph, The graph evaluates the quality of clustering by measuring the similarity to each data point and to its assigned cluster against other clusters. As a result of this the vertical dashed line indicates the optimal number of clusters for the preprocessed data set.  
2.4 Performing k-means algorithm for 2 and 3 clusters.
Based on the elbow and silhouette method it is evident that the ideal number of clusters are 2 and 3. Therefore, performing k-means algorithm on two and three clusters (Appendix 2.4.1). 
 
Figure 5 Cluster Plot (2 Clusters)

 
Figure 6 Cluster Plot (3 Clusters)

The above two cluster plots visually represent on a cluster plot. Based on the two plots, its visible that two clusters do not have any overlaps and 3 clusters also has an overlap between cluster 1 and 3. 
2.5 Validating 2 and 3 Clusters.
To determine which clustering test is more accurate by using the silhouette score, where it helps to measures how similar an object is to its own cluster compared to other clusters. This will better help to determine the validation (Appendix 2.5.1). Based on the output, 2 clusters: 1.6513 and for 3 clusters: 0.2918397. Based on the output 2 clusters provides a higher score than 3 clusters. 
In addition to further validate, using Hubert Index and D index to determine the optimal number of clusters. By using the NbClust function and setting the distance as Euclidean distance and setting the parameters for minimum clusters as two and maximum as ten, while using k-means algorithm (Appendix 2.5.2).
 
Figure 7 Output of NbClust Funcation
Based on the above given output, the best number of clusters are recognized as 2 based on the majority rule. 
2.6 Calculating the mean of each attribute of each group.
To calculate the mean of each attribute of two clusters. Which represents the average values of all the features for the data points (Appendix 2.6.1). 
 
Figure 8 Output of Mean of Each Attribute (C2)
Each row of the given output represents the mean value for each attribute selected for cluster 2. These values provide information on the distance of the data points for cluster 2 and see if any distinguishing values that may separate the clusters. Therefore, to further investigate, visualizing the mean of each attribute (Appendix 2.6.2). 
 
Figure 9 Heatmap Mean Values
Based on the above heatmap the highest mean is for the attribute “Pr.Axis.Rect” and the smalles mean is for “Kurt.Maxis”. Furthermore, “Elong” attribute is the closest attribute to zero and that values of the attribute are distributed around the mean. 
2.7 Checking the results against the Class Attribute
After preprocessing and determining the winning clusters it is important to cross validate the given results against the initial class attribute values (Appendix 2.7.1).

 
Figure 10 Cluster Plot (2 Clusters) with Class Attribute
Based on the above visualization, the two clusters are visible well separated with a few minor overlaps. Based on that it is evident that the clusters are well separated among one another in comparison to three clusters, which is shown in the below illustration. Where cluster 1 and 3 have large overlaps.
 
Figure 11 Cluster Plot (3 Clusters) with Class Attribute
2.8 Calculating Cluster Purity Score.

To validate the above given two clusters, it is required to calculate the cluster purity score. This compares the cluster labels with the original class labels across each data point. As a result of this, it will measure how well the clustering algorithm has grouped similar observations among one another (Appendix 2.8.1). 
 
Figure 12 Output Cluster Purity Score
Based on the output, the cluster purity score was 0.65 represents that 65% of the data points are correctly classified against the original data set.
2.9 Data Pre-Processing.
Based on the initial preprocessed data set apart from cleaning and checking and removing any outliers. The 18 attributes may not be relevant. Therefore, to determine what attributes are required by using principal component analysis (Appendix 2.9.1). 
 
Figure 13 Scree Plot of Principal Component Analysis
Based on the above scree plot in it is visible that most of the attributes are not required. Therefore, selected the top 5 attributes from descending order. The dotted area represents the selected attributes and creates a new data frame for further clustering (Appendix 2.9.2). 


2.10 Analyzing the Pre-Processes Data
Based on the new data frame that was generated after performing PCA. This was predominantly done to reduce the data set. 
After scaling the data set once again, the data was evaluated on elbow and Silhouette method to determine the ideal number of clusters. Both methods resulted in two clusters. 
 
Figure 14 Silhouette Method Plot
 
Figure 15 Elbow Method Plot

Thereafter the winning clusters are visualized on a cluster plot based on the two clusters.
 
Figure 16 Cluster Plot for Top 5 Attributes
After performing PCA and reducing the number of attributes has given a more concise cluster plot. This clearly demarcates the two clusters among one another. 
Upon further investigation, to calculate the similarity among two clustering results. The original data set and the data set that is derived after performing PCA is compared to identify and benchmark the score adjusted rand index is used (Appendix 2.10.1). As result of performing ARI score resulted in 0.8188801. This represents that the clustering results are highly relatable. 
 
Figure 17 Adjusted Rand Index Score
Based on the clustering analysis and objectives, it is evident that the vehicle dataset can be divided into two clusters. Data cleaning, preprocessing, and cross-validation were performed to generate the clusters, and it was found that the most appropriate number of clusters was two. Additionally, irrelevant attributes were removed, and the clustering analysis still resulted in two clusters. Therefore, the vehicle dataset can be accurately clustered into two groups, and the clusters can be used to identify and analyze patterns within the dataset.
