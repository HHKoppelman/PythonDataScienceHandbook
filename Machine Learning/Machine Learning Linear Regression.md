# Machine Learning: Linear Regression
#DataScience/Handbook/MachineLearning


> Linear Regression: Fit quickly, very interpretable  

Linear Regression on multi-dimensional data
>  Geometrically, this is akin to fitting a plane to points in three dimensions, or fitting a hyper-plane to points in higher dimensions.  

```python
sklearn.linear_model.LinearRegression
# Doc string: Ordinary least squares Linear Regression.
```


### Powerful adaption: Basis Function Regression
Transform your input data according to some basis function (e.g. the `PolynomialRegression` example from previous notebook).

![](Machine%20Learning%20Linear%20Regression/A375AE83-445F-4CD7-9F78-785FB5D12D07.png)
With
![](Machine%20Learning%20Linear%20Regression/AB4D2501-6CE0-4007-AC65-4160A676EFD4.png)

This results in Polynomial regression if
![](Machine%20Learning%20Linear%20Regression/A87097A5-997D-4177-BFA8-CA49093C9E7D.png)


### Gaussian basis functions
```python
from sklearn.base import BaseEstimator, TransformerMixin

class GaussianFeatures(BaseEstimator, TransformerMixin):
    """Uniformly spaced Gaussian features for one-dimensional input"""

    def __init__(self, N, width_factor=2.0):
        self.N = N
        self.width_factor = width_factor

    @staticmethod
    def _gauss_basis(x, y, width, axis=None):
        arg = (x - y) / width
        return np.exp(-0.5 * np.sum(arg ** 2, axis))

    def fit(self, X, y=None):
        # create N centers spread along the data range
        self.centers_ = np.linspace(X.min(), X.max(), self.N)
        self.width_ = self.width_factor * (self.centers_[1] - self.centers_[0])
        return self

    def transform(self, X):
        return self._gauss_basis(X[:, :, np.newaxis], self.centers_,
                                 self.width_, axis=1)

gauss_model = make_pipeline(GaussianFeatures(20),
                            LinearRegression())
gauss_model.fit(x[:, np.newaxis], y)
yfit = gauss_model.predict(xfit[:, np.newaxis])

plt.scatter(x, y)
plt.plot(xfit, yfit)
plt.xlim(0, 10);
```
The code above creates a superposition of uniformly-spaced Gaussians
![](Machine%20Learning%20Linear%20Regression/unknown.png)


### Regularization: `Lasso`, `Ridge`, and `ElasticNet`
Lasso regularization has the benefit that it tends to set unnecessary coefficients to zero
ElasticNet is a (linear) combination of Lasso and Ridge.
```python
from sklearn.linear_model import Lasso, Ridge, ElasticNet

no_reg = make_pipeline(GaussianFeatures(30), LinearRegression())
lasso = make_pipeline(GaussianFeatures(30), Lasso(0.01))
ridge = make_pipeline(GaussianFeatures(30), Ridge(0.01))
elastic = make_pipeline(GaussianFeatures(30), ElasticNet(0.01))

models = [no_reg, lasso, ridge, elastic]

plt.figure(figsize=(10,8))
for model in models:

    model.fit(x[:, np.newaxis], y)
    yfit = model.predict(xfit[:, np.newaxis])
    plt.plot(xfit, yfit, label=model.get_params()['steps'][-1][0].replace('rr','r r'))

plt.legend(frameon=True)
plt.scatter(x, y, zorder=0)
plt.xlim(0, 10);
```
![](Machine%20Learning%20Linear%20Regression/unknown%202.png)
