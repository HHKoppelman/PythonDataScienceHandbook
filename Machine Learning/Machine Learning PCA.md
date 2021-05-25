# Machine Learning: PCA
#DataScience/Handbook/MachineLearning

PCA finds the axis of maximum variance. It can be used as feature selection, but also as noise suppression!

> PCA is fundamentally a dimensionality reduction algorithm, but it can also be useful as a tool for visualization, for noise filtering, for feature extraction and engineering, and much more.   

> This transformation from data axes to principal axes is an _affine transformation_, which basically means it is composed of a translation, rotation, and uniform scaling.  

Example of PCA
![](Machine%20Learning%20PCA/unknown.png)


## A few examples of applying PCA to images:
Cleaning noisy digits:
![](Machine%20Learning%20PCA/unknown%202.png)
![](Machine%20Learning%20PCA/unknown%203.png)

Faces:
![](Machine%20Learning%20PCA/unknown%204.png)

## Summary
> PCA’s main weakness is that it tends to be highly affected by outliers in the data.  
> For this reason, many robust variants of PCA have been developed, many of which act to iteratively discard data points that are poorly described by the initial components. Scikit-Learn contains a couple interesting variants on PCA, including `RandomizedPCA` and `SparsePCA`.  

> `RandomizedPCA`, which we saw earlier, uses a non-deterministic method to quickly approximate the first few principal components in very high-dimensional data, while `SparsePCA` introduces a regularization term (see  [In Depth: Linear Regression](https://jakevdp.github.io/PythonDataScienceHandbook/05.06-linear-regression.html) ) that serves to enforce sparsity of the components.  
