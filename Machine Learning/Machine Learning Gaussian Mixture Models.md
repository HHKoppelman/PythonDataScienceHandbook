# Machine Learning: Gaussian Mixture Models
#DataScience/Handbook/MachineLearning

K-means clustering is great; except for non-spherical clusters
For example, comparing the two cases 
![](Numpy%20Python%20data%20types/209ACBE4-1990-4E20-83AE-30320803D51D.png)	and		![](Numpy%20Python%20data%20types/61D44DD1-533D-44EF-92B7-B6FBF4BD7805.png)

Also k-means clustering is absolute: a data point either belongs to a cluster or it does not.

Gaussian Mixture Models can be regarded to as generalizations of k-means clustering:
	* They incorporate probabilities in the form of distances to all clusters;
	* and they work on the basis of ellipses rather than circles.

> Under the hood, a Gaussian mixture model is very similar to k-means: it uses an expectation–maximization approach which qualitatively does the following:  
> 	1. Choose starting guesses for the location and shape  
> 	2. Repeat until converged:  
> 		E-step:	for each point, find weights encoding the probability of membership  
> 		 		in each cluster  
> 		M-step:	for each cluster, update its location, normalization, and shape based  
> 				on all data points, making use of the weights  

The GMM example of the problem above
![](Numpy%20Python%20data%20types/61365F51-1E5E-4749-B132-855B3B87C7BF.png)

Not sure why, but GMMs allow one to force the covariance matrix to be diagonal or even isotropic
![](Numpy%20Python%20data%20types/05.12-covariance-type.png)

### How many components?
Is an often asked question. There exist several criterion to decide when to stop adding components. For example, there are the [Akaike information criterion (AIC)](https://en.wikipedia.org/wiki/Akaike_information_criterion) and the [Bayesian information criterion (BIC)](https://en.wikipedia.org/wiki/Bayesian_information_criterion). 

::NB:::
> Notice the important point: this choice of number of components measures how well GMM works as a density estimator, not how well it works as a clustering algorithm. I’d encourage you to think of GMM primarily as a density estimator, and use it for clustering only when warranted within simple datasets.  

## Example: GMM to generate new data
These are randomly generated digits of the digits data set
![](Numpy%20Python%20data%20types/A0F4DAFB-C7D8-4252-8EEF-0F91D122AEF8.png)