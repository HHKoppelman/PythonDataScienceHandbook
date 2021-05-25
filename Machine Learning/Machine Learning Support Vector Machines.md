# Machine Learning: Support Vector Machines
#DataScience/Handbook/MachineLearning

SVMs are a tool for _discriminative classification_
That is, they find a line or surface that separates classifiers. Often there is no unique such divider, so the SVM aims to find the divider with the largest margin:
![](Numpy%20Python%20data%20types/unknown.png)

> Support vector machines are an example of such a _maximum margin_ estimator.  

The _support vectors_ are the data points that define the maximum margin
![](Numpy%20Python%20data%20types/unknown%202.png)
**NB**: Only the support vectors matter to the fit; adding data points that are outside of the margin will _not_ change the fit.

## Powerful option: non-linear kernels

The `sklearn` RBF has the following form

![](Numpy%20Python%20data%20types/E6BC05C7-D36B-4C8E-A320-B4C47CF964D6.png)

which is known as the kernel trick: for some kernel $\phi(x)$ the _kernel function_ describes the dot product between two kernel vectors

![](Numpy%20Python%20data%20types/690A41F0-B902-4234-AA05-4A4B2CE289C6.png)

SVMs make use of the fact that the exact form of the kernel does not have to be specified (i.e. in the case of the RBS the origin is unknown). However, by SVMs **linearly** separate the classes in the transformed kernel space using the kernel function.

## SVM fudge factor `C`
A small C allows points to be within the margin if that improves the fit. Large C-values prevent this.

> The optimal value of the C parameter will depend on your dataset, and should be tuned using cross-validation or a similar procedure.  
![](Numpy%20Python%20data%20types/unknown%203.png)


## SVM: the summary

SVMs are powerful because:
* Their dependence on relatively few support vectors means that they are very compact models, and take up very little memory.
* Once the model is trained, the prediction phase is very fast.
* Because they are affected only by points near the margin, they work well with high-dimensional data—even data with more dimensions than samples, which is a challenging regime for other algorithms.
* Their integration with kernel methods makes them very versatile, able to adapt to many types of data.

Their disadvantages are:
* The scaling with the number of samples N is O[N^3] at worst, or O[N^2] for efficient implementations. For large numbers of training samples, this computational cost can be prohibitive.
* The results are strongly dependent on a suitable choice for the softening parameter C. This must be carefully chosen via cross-validation, which can be expensive as datasets grow in size.
* The results do not have a direct probabilistic interpretation. This can be estimated via an internal cross-validation (see the probability parameter of SVC), but this extra estimation is costly.








