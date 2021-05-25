# Machine Learning: Manifold Learning
#DataScience/Handbook/MachineLearning

PCA: flexible and easy to interpret; but does not deal well with non-linear data
Manifold Learning: aims to embed a high-dimensional distribution in a low-dimensional representation.

## Multidimensional Scaling (MDS)
Represents a data set from its distance matrix
Original data
![](Machine%20Learning%20Manifold%20Learning/unknown.png)
MDS 2-dimensional representation of the distance matrix `D`
![](Machine%20Learning%20Manifold%20Learning/unknown%202.png)

Of course the power of this kind of learning lies in representing D-dimensional data (with D>2) on a 2-dimensional manifold.

Where MDS fails: non-linear data
![](Machine%20Learning%20Manifold%20Learning/unknown%203.png)
Is represented as
![](Machine%20Learning%20Manifold%20Learning/unknown%204.png)

The problem arises from the MDF trying to preserve distance _globally_.

## Locally Linear Embedding
Aims to preserve distances only _locally_ which allows for embedding of non-linear manifolds.

MDS vs LLE
![](Machine%20Learning%20Manifold%20Learning/05.10-LLE-vs-MDS.png)

The same S-curved hello data in LLE
![](Machine%20Learning%20Manifold%20Learning/unknown%205.png)
Looks a lot better
But see LLE with a different method (`ltsa` in stead of `modified`)
![](Machine%20Learning%20Manifold%20Learning/unknown%206.png)


## Summary
> Though this story and motivation is compelling, in practice manifold learning techniques tend to be finicky enough that they are rarely used for anything more than simple qualitative visualization of high-dimensional data.  

In contrast to PCA:
* In manifold learning, there is no good framework for handling missing data. In contrast, there are straightforward iterative approaches for missing data in PCA.
* In manifold learning, the presence of noise in the data can “short-circuit” the manifold and drastically change the embedding. In contrast, PCA naturally filters noise from the most important components.
* The manifold embedding result is generally highly dependent on the number of neighbors chosen, and there is generally no solid quantitative way to choose an optimal number of neighbors. In contrast, PCA does not involve such a choice.
* In manifold learning, the globally optimal number of output dimensions is difficult to determine. In contrast, PCA lets you find the output dimension based on the explained variance.
* In manifold learning, the meaning of the embedded dimensions is not always clear. In PCA, the principal components have a very clear meaning.
* In manifold learning the computational expense of manifold methods scales as O[N^2] or O[N^3]. For PCA, there exist randomized approaches that are generally much faster (though see the  [megaman](https://github.com/mmp2/megaman)  package for some more scalable implementations of manifold learning).

> With all that on the table, the only clear advantage of manifold learning methods over PCA is their ability to preserve nonlinear relationships in the data; for that reason I tend to explore data with manifold methods only after first exploring them with PCA.  

* For toy problems such as the S-curve we saw before, locally linear embedding (LLE) and its variants (especially modified LLE), perform very well. This is implemented in `sklearn.manifold.LocallyLinearEmbedding`.
* For high-dimensional data from real-world sources, LLE often produces poor results, and isometric mapping (IsoMap) seems to generally lead to more meaningful embeddings. This is implemented in `sklearn.manifold.Isomap`
* For data that is highly clustered, t-distributed stochastic neighbor embedding (t-SNE) seems to work very well, though can be very slow compared to other methods. This is implemented in `sklearn.manifold.TSNE`.
