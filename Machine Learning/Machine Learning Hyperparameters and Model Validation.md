# Machine Learning: Hyperparameters and Model Validation
#DataScience/Handbook/MachineLearning


	1. Choose a class of model
	2. Choose model hyperparameters
	3. Fit the model to the training data
	4. Use the model to predict labels for new data


### Cross validation

Scikit-Learn’s k-fold cross validation
```python
from sklearn.cross_validation import cross_val_score
cross_val_score(model, X, y, cv=5)
```

Leave-one-out cross validation, for really small data sets
```python
from sklearn.cross_validation import cross_val_score, LeaveOneOut
scores = cross_val_score(model, X, y, cv=LeaveOneOut(len(X)))
scores
```


### The learning curve
Is a tool to test whether the model complexity is sufficient.
![](Machine%20Learning%20Hyperparameters%20and%20Model%20Validation/05.03-learning-curve.png)

Using a learning curve to find model convergence:
`from sklearn.learning_curve import learning_curve`
![](Machine%20Learning%20Hyperparameters%20and%20Model%20Validation/unknown.png)
The second degree polynomial converges at a very low number of data points; clearly adding more data does not add more information! Only way to improve the 2-degree model is to use a different and more complex model!

### Grid Search
Systematically explores the parameter landscape to find the best model parameters.

For example
```python
from sklearn.grid_search import GridSearchCV

param_grid = {'polynomialfeatures__degree': np.arange(21),
              'linearregression__fit_intercept': [True, False],
              'linearregression__normalize': [True, False]}

grid = GridSearchCV(PolynomialRegression(), param_grid, cv=7)
grid.fit(X, y);
print(grid.best_params_)
```

Reference:
[Hyperparameters and Model Validation | Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/05.03-hyperparameters-and-model-validation.html)
