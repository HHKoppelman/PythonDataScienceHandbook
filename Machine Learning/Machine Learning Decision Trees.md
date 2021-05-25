# Machine Learning: Decision Trees
#DataScience/Handbook/MachineLearning

Decision trees are a tool for _non-parametric classification_
> Random forests are an example of an ensemble method, meaning that it relies on aggregating the results of an ensemble of simpler estimators.   

Example of steps taken by a Decision Tree Classifier
![](Machine%20Learning%20Decision%20Trees/05.08-decision-tree-levels.png)
Several steps (and a different colour scheme) further
![](Machine%20Learning%20Decision%20Trees/unknown.png)

**NB**: if with increasing depth the trees become increasingly more complex. Perhaps even with some pathological behavior, see this example
![](Machine%20Learning%20Decision%20Trees/unknown%202.png)

Decision trees are likely to overfit: that’s where bagging comes in
> Bagging makes use of an ensemble (a grab bag, perhaps) of parallel estimators, each of which over-fits the data, and averages the results to find a better classification. An ensemble of randomized decision trees is known as a random forest.  

Example of manual bagging in `sklearn`
```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import BaggingClassifier

tree = DecisionTreeClassifier()
bag = BaggingClassifier(tree, n_estimators=100, max_samples=0.8,
                        random_state=1)

bag.fit(X, y)
```

The results looks more organic but still slightly overfitted
 ![](Machine%20Learning%20Decision%20Trees/unknown%203.png)

`BaggingClassifier` docstring:
> A Bagging classifier is an ensemble meta-estimator that fits base  
> classifiers each on random subsets of the original dataset and then  
> aggregate their individual predictions (either by voting or by averaging)  
> to form a final prediction. Such a meta-estimator can typically be used as  
> a way to reduce the variance of a black-box estimator (e.g., a decision  
> tree), by introducing randomization into its construction procedure and  
>  then making an ensemble out of it.  

## Random forest regression
Not sure what the benefit is of RF regression, except for it being non-parametric.
![](Machine%20Learning%20Decision%20Trees/unknown%204.png)

## Example: Classification of Digits
The Random Forrest Classifier is very accurate!
![](Machine%20Learning%20Decision%20Trees/29C8A9BC-DBDE-46C4-9E77-2A687B782524.png)

## Summary
Ensemble estimators, such as the random forest, are very fast to train and predict.

* Both training and prediction are very fast, because of the simplicity of the underlying decision trees. In addition, both tasks can be straightforwardly parallelized, because the individual trees are entirely independent entities.
* The multiple trees allow for a probabilistic classification: a majority vote among estimators gives an estimate of the probability (accessed in Scikit-Learn with the `predict_proba()` method).
* The nonparametric model is extremely flexible, and can thus perform well on tasks that are under-fit by other estimators.

Disadvantage: they can be complex and are prone to overfit.
> A primary disadvantage of random forests is that the results are not easily interpretable: that is, if you would like to draw conclusions about the meaning of the classification model, random forests may not be the best choice.  
