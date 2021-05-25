# Machine Learning: Naive Bayes
#DataScience/Handbook/MachineLearning

> Extremely fast and simple classification  
> Ideal for quick-and-dirty baselines  

A Bayes classifier aims to fit a generative model to the data. 
The simplest example is Gaussian Naive Bayes

> Naive Bayes (NB) is **naive** because it makes the assumption that features of a measurement are independent of each other. This is naive because it is (almost) never true.   

::Does Gaussian Naive Bayes without priors just calculate mean and std for each class?::
Yes. Source code for  `sklearn.naive_bayes.GaussianNB` just calculates the mean and standard deviation in a lazy and out-of-core way to be able to classify large data sets that do not fit into memory.


Advantages
	* They are extremely fast for both training and prediction
	* They provide straightforward probabilistic prediction
	* They are often very easily interpretable
	* They have very few (if any) tunable parameters

Performs well
	* When the naive assumptions actually match the data (very rare in practice)
	* For very well-separated categories, when model complexity is less important
	* For very high-dimensional data, when model complexity is less important
