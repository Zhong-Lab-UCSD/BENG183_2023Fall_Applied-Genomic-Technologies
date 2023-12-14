# Hierarchical Clustering

## Overview
1. What is Clustering?
2. Hierarchical Clustering Techniques
3. Calculating Similarity
4. Different Ways to Measure Distance
5. Limitations of Hierarchical Clustering
6. Significance of Hierarchical Clustering
7. Hierarchical Clustering Applications
8. Other Types of Clustering
9. References

## What is Clustering?

### Clustering vs. Classification/Regression

Clustering is an **unsupervised machine learning method**, because the input dataset conists of only **data points with no labels**. There usually are not separate training and testing datasets in clustering and other unsupervised learning methods, so the input data is the data of interest. Due to the unsupervised nature of clustering, it is used to **uncover relationships within the data that may not be otherwise observed**. The overall goal of clustering is to, given a set of *n* data points, group those data points into a previously undefined *k* number of clusters, where the **objects belonging to each cluster are more similar to each other than to those outside of the cluster**. 

In comparison, classification and regression are **supervised machine learning methods**, because those models are trained and tested on datasets that conist of both **data points and labels**. As alluded to, the input dataset is split in to **a training set and a testing set**. The corresponding model is then applied to data with no labels to make predictions based on its learned specifications.

## Hierarchical Clustering Techniques

### Agglomerative Clustering (Bottom-Up Approach)

Initially, consider each data point to be in its own individual cluster.

1. Calculate the distance between each pair of clusters to create a proximity matrix.
2. Merge the two closest clusters and update the matrix.
3. Repeat step 2 until all the data points are in one cluster.

Data can be represented with a dendrogram, which shows visually where the data merged and split:

<img width="500" alt="Cluster_types" src="https://github.com/ellaksay/BENG183/blob/main/dendrogram.jpeg">

### Divisive Clustering (Top-Down Approach)

Initially, conider all data points to be in one cluster.
1. Split the cluster using a flat clustering method, such as K-means.
2. Among all the clusters, choose the "best\"* one to split. \*divisive clustering requires a method that decides which is the "best" cluster
3. Split the chosen cluster using the same flat clustering method.
4. Repeat steps 2 and 3 until each data point is in its own cluster.

## Calculating Similarity

A key step in both agglomerative and divisive clustering is calculating the similarities between clusters. How do we do this?

### Min Distance (Single-Linkage Algorithm)

    *similar(A1,A2) = Min similar(Bi,Bj) such that Bi ∈ A1 & Bj ∈ A2*

Take the two closest points in each cluster, calculate their distance, and declare that to be the similarity of the two clusters.

<img width="300" alt="Clustering3" src="https://github.com/b1sanchez/BENG183/assets/96998684/e6951f68-7066-4621-ad34-54e97064c30a">

**Pro** of single-linkage is that it can be used to calculate the distance between clusters that are not necessarily elliptical. 

**Con** of single-linkage is that it is sensitive to noise (can't properly separate clusters if there is noise between them).

### Max Distance (Complete-Linkage Algorithm)

    *similar(A1,A2) = Max similar(Bi,Bj) such that Bi ∈ A1 & Bj ∈ A2*

Take the two farthest points in each cluster, calculate their distance, and declare that to be the similarity of the two clusters.

<img width="300" alt="Clustering2" src="https://github.com/b1sanchez/BENG183/assets/96998684/1899541b-f2c4-4025-a137-150e3944e9b7">

**Pro** of complete-linkage is that it is not sensitive to noise.

**Cons** of complete-linkage are that it is biased towards creating globular clusters, and it tends to break large clusters into multiple clusters.

### Mean Distance (UPGMA)

    *similar(A1,A2) = ∑ similar(Bi, Bj)/|A1|x|A2 where, Bi ∈ A1 & Bj ∈ A2*

Take all pairs of points between the two clusters and calculate their distances. Then calculate the average of those distances across the two clusters and declare that to be the similarity of the two clusters.

<img width="300" alt="Clustering1" src="https://github.com/b1sanchez/BENG183/assets/96998684/7442a8e0-054e-4e28-9f51-d0b432ae2f03">

**Pro** of mean distance is that it is not sensitive to noise.

**Con** of mean distance is that it is biased towards creating globular clusters.

## Different Ways to Measure Distance 

All three of the similarity measures discussed above depend on distance calculations. What are two of the most popular metrics for calculating distance?

### Euclidean Distance

Euclidean distance represents the shortest distance between two points, and it is calculated using the principle of the Pythagorean theorem. In many machine learning algorithms, it is the default distance metric. However, it requires the data points to have continuous, numeric features.

To calculate the Euclidean distance between two data points, *x* and *y*, in an n-dimensional space:
$$Euclidean(x,y) = \sqrt{\sum_{i=1}^n (x_i-y_i)^2}$$
  
<img width="500" alt="Euclidean Distance Visual" src="https://d2mk45aasx86xg.cloudfront.net/image1_11zon_fa4497e473.webp">

### Manhattan Distance

Manhattan distance (aka cityblock distance) calculates the distance between the coordinates of two points using a grid-like path. This metric is more effective when the data points have discrete or binary features.

To calculate the Manhattan distance between two data points, *x* and *y*, in an n-dimensional space:
$$Manhattan(x,y) = \sum_{i=1}^n |x_i-y_i|$$

<img width="500" alt="Manhattan Distance Visual" src="https://d2mk45aasx86xg.cloudfront.net/image5_11zon_7723f44a19.webp">

## Limitations of Hierarchical Clustering

The time-complexity for hierarchical clustering is very high, making it inefficient for large datasets. All three of the main ways to calculate similarity are flawed in their own ways, which in turn makes hierarchical clustering as a whole an imperfect method. 

## Significance of Hierarchical Clustering
1) High Accuracy
   - Reliable and accurate results
3) Flexible
   - Can be used on any type of data
4) Optimial Generalization 
   - Creates clusters based on the similarity between the objects rather than predetermined classifications

## Hierarchical Clustering Applications

Here are a few example bioinformatics questions that can be investigated using hierarchical clustering:
1. Which genes are similar to each other across different experimental conditions and/or across different samples based on their expression levels?
2. Are there different subtypes of cancer present in these samples based on their molecular signatures?
3. Are there different subpopulations of patients who respond differently to a given drug based on their transcriptomic profiles?

## Other Types of Clustering
Here are brief descriptions of two other popular clustering algorithms:
1. K-means clustering: declares the *k* number of clusters from the start and places each data point in the nearest cluster while minimizing the size of the clusters. 
2. Density-based clustering: creates clusters based off of density rather than absolute distance.

There are many other clustering algorithms as well! See all the world has to offer below:
![Other Clustering Methods](https://github.com/ellaksay/BENG183/blob/main/clusters.png)

## References
1. UCSD BENG 183 Lecture Slides
2. [Advantages of Hierarchical Clustering](https://codinginfinite.com/hierarchical-clustering-applications-advantages-and-disadvantages/)
3. [Cluster Image](https://www.google.com/url?sa=i&url=https%3A%2F%2Ftowardsdatascience.com%2Fthe-5-clustering-algorithms-data-scientists-need-to-know-a36d136ef68&psig=AOvVaw0wY-QUMLK4uLpdMVm4kBDQ&ust=1702495156854000&source=images&cd=vfe&opi=89978449&ved=0CBIQjRxqFwoTCNC-i-vOioMDFQAAAAAdAAAAABAD)
4. [Dendrogram Image](https://www.google.com/url?sa=i&url=https%3A%2F%2Fforum.knime.com%2Ft%2Fhierarchical-clustering-dendrogram%2F19313&psig=AOvVaw205Do-bZLCXVUx8sNdeEZw&ust=1702495390876000&source=images&cd=vfe&opi=89978449&ved=0CBIQjRxqFwoTCLDmr-LPioMDFQAAAAAdAAAAABAD)
5. [Understanding Hierarchical Clustering](https://towardsdatascience.com/understanding-the-concept-of-hierarchical-clustering-technique-c6e8243758ec)
6. [Hierarchical Clustering in Machine Learning](https://www.geeksforgeeks.org/ml-hierarchical-clustering-agglomerative-and-divisive-clustering/)
7. [Latex Equations](https://github.com/rasbt/pattern_classification/blob/master/resources/latex_equations.md#distance-euclidean)
8. [How to Decide the Perfect Distance Metric For Your Machine Learning Model](https://www.turing.com/kb/how-to-decide-perfect-distance-metric-for-machine-learning-model)
9. [Hierarchical Clustering Analysis](https://bmb.cd-genomics.com/hierarchical-clustering-analysis.html)
