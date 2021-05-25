# Machine Learning: Kernel Density Estimation
#DataScience/Handbook/MachineLearning

Gaussian kernel estimate of a 1D distribution
![](Machine%20Learning%20Kernel%20Density%Estimation/99E96D83-215B-4DE0-B489-84E23C4701B3.png)

### What bandwidth should one use?
One way of assessing this problem is by using cross-validation!


CV with LeaveOneOut
```python
from sklearn.model_selection import GridSearchCV
from sklearn.model_selection import LeaveOneOut
from sklearn.neighbors import KernelDensity

# Making the data
def make_data(N, f=0.3, rseed=1):
    rand = np.random.RandomState(rseed)
    x = rand.randn(N)
    x[int(f * N):] += 5
    return x
x = make_data(20)

# Running the CV
bandwidths = 10 ** np.linspace(-1, 1, 100)
grid = GridSearchCV(KernelDensity(kernel='gaussian'),
                    {'bandwidth': bandwidths},
                    cv=LeaveOneOut())
grid.fit(x[:, None]);
print(grid.best_params_)
```


## KDE example: points on a sphere
> we will use the haversine distance metric which will correctly represent distances on a curved surface.   
The example
![](Machine%20Learning%20Kernel%20Density%Estimation/6A325DFD-D0B4-48B2-B467-83FBF1FEB2FC.png) versus the original ![](Machine%20Learning%20Kernel%20Density%Estimation/C9BB5C12-A0F9-4A3E-9AF6-4F6D8EE4CDDD.png)


## KDE example: KDE classifier
> With a density estimation algorithm like KDE, we can remove the "naive" element and perform the same classification with a more sophisticated generative model for each class. It's still Bayesian classification, but it's no longer naive.  
Results
![](Machine%20Learning%20Kernel%20Density%Estimation/D9B33FE6-7939-4FB2-86DE-0C0E070ADF7B.png)
> We see that this not-so-naive Bayesian classifier reaches a cross-validation accuracy of just over 96%; this is compared to around 80% for the naive Bayesian classification  
