# Machine Learning: k-Means
#DataScience/Handbook/MachineLearning

k-Means applies expectation maximization to most optimally place the k markers.

Expectation-Maximization:
	1. Guess some cluster centers
	2. Repeat until converged
		1. E-Step: assign points to the nearest cluster center
		2. M-Step: set the cluster centers to the mean

![](Numpy%20Python%20data%20types/05.11-expectation-maximization.png)


Two possible caveats are that the algorithm can converge on a local optimal solution; not global
![](Numpy%20Python%20data%20types/unknown.png)
And that the number of clusters must be selected beforehand
![](Numpy%20Python%20data%20types/unknown%202.png)

The former can be overcome by running the algorithm several times initiating the walkers from different locations.

Several other clustering algorithms exist;
For example, `GaussianMixtureModels` have better quantitative measures of finding the clusters. On the other hand, `DBSCAN`, `mean-shift`, and `affinity propagation` all do not require the number of clusters to be specified beforehand.

Another caveat of k-means are complex structures
![](Numpy%20Python%20data%20types/unknown%203.png)

Similar to what we have done before (i.e. projecting the data into a higher dimensional space) we can use `SpectralClustering` to cluster on the graph of nearest neighbors in stead of just on the data
```python 
from sklearn.cluster import SpectralClustering
model = SpectralClustering(n_clusters=2, affinity='nearest_neighbors',
                           assign_labels='kmeans')
```
![](Numpy%20Python%20data%20types/unknown%204.png)
NB: not specifying the `affinity` and `assign_labels` here will result in the same clustering as just `k-means`
![](Numpy%20Python%20data%20types/unknown%205.png)

`k-means` can be slow for large data sets because it requires the calculated the pair-wise distances iteratively. One form that aims to overcome this and is implemented in sklearn is `sklearn.cluster.MiniBatchKMeans`

### Example 1: digits (unsupervised!!)
These are the 10 means found by the k-means algorithm with k=10
![](Numpy%20Python%20data%20types/unknown%206.png)
The overall labeling has an accuracy of 80% which is not bad considering the simplicity of k-means and the fact that it is completely unsupervised!

These are the centers for the faces:
![](Numpy%20Python%20data%20types/unknown%207.png)
For faces this does not work so well


### Example 2: colour compression
Original colors of the image:
![](Numpy%20Python%20data%20types/unknown%208.png)
The above space contains 256x256x256 = 16_777_216  possible colours – however most of the space is empty!

Using k-means with 16 clusters we can refactor the space
![](Numpy%20Python%20data%20types/unknown%209.png)

The result:
![](Numpy%20Python%20data%20types/unknown%2010.png)














