# Machine Learning: Feature Engineering
#DataScience/Handbook/MachineLearning

Is one of the more important steps of ML!

Creating a large structured version of your data set is known as **vectorization**


Some examples for categorial data, text, and images.

## Categorial Features
Mapping categories to numbers: generally **not** a good idea!
`{'Queen Anne': 1, 'Fremont': 2, 'Wallingford': 3};`
> Such a mapping would imply, for example, that `Queen Anne < Fremont < Wallingford`, or even that `Wallingford - Queen Anne = Fremont`, which (niche demographic jokes aside) does not make much sense.  

Better to use _one-hot-encoding_
```python
from sklearn.feature_extraction import DictVectorizer
vec = DictVectorizer(sparse=False, dtype=int)
vec.fit_transform(data)
```
The above `sklearn` function only one-hot encodes column of `dtype=int`.

To retrieve the feature names
`vec.get_feature_names()`

Use a spare representation if there are too many columns
```python
vec = DictVectorizer(sparse=True, dtype=int)
vec.fit_transform(data)
```
Vec -> because vectorized data set (see top of note)

Similar `sklearn` tools
```python
sklearn.preprocessing.OneHotEncoder
sklearn.feature_extraction.FeatureHasher
```


## Text Features
Count vectorizer: counts all occurrences of words
```python
sample = ['problem of evil',
          'evil queen',
          'horizon problem']

from sklearn.feature_extraction.text import CountVectorizer

vec = CountVectorizer()
X = vec.fit_transform(sample)
X
```

This might overrepresent words that appear often in documents/strings. 
> One approach to fix this is known as term frequency-inverse document frequency (TF–IDF) which weights the word counts by a measure of how often they appear in the documents.   
```python
from sklearn.feature_extraction.text import TfidfVectorizer
vec = TfidfVectorizer()
X = vec.fit_transform(sample)
pd.DataFrame(X.toarray(), columns=vec.get_feature_names())
```

## Derived Features
One simple way to fit a non-linear relation using `LinearRegression` is to polynomify the input
```python
from sklearn.preprocessing import PolynomialFeatures
poly = PolynomialFeatures(degree=3, include_bias=False)
X2 = poly.fit_transform(X)

# Fitting a LinearRegression
model = LinearRegression().fit(X2, y)
yfit = model.predict(X2)
plt.scatter(x, y)
plt.plot(x, yfit);
```
![](Numpy%20Python%20data%20types/unknown.png)
As we see, the resulting fit (which looks piece-wise but this is only because of the discrete input) uses linear regression to find a third order polynomial. The resulting fit remains linear in the model parameters, e.g. `y_fit = a*x + b*x^2 + c*x^3`

## Missing Features
Simplest way to deal with missing data is to use a mean imputer
```python
from numpy import nan
X = np.array([[ nan, 0,   3  ],
              [ 3,   7,   9  ],
              [ 3,   5,   2  ],
              [ 4,   nan, 6  ],
              [ 8,   8,   1  ]])

from sklearn.impute import SimpleImputer
imp = SimpleImputer(strategy='mean')
X2 = imp.fit_transform(X)
```

Or a k-nearest imputer
```python
from sklearn.impute import KNNImputer
imputer = KNNImputer(n_neighbors=2)
X3 = imputer.fit_transform(X)
```

## Creating Pipelines
An example pipeline to:
	1. Impute missing values using the mean
	2. Transform features to quadratic
	3. Fit a linear regression

```python
from sklearn.pipeline import make_pipeline

# Constructing the pipeline
model = make_pipeline(Imputer(strategy='mean'),
                      PolynomialFeatures(degree=2),
                      LinearRegression())

# Deploying the model
model.fit(X, y)  # X with missing values, from above
print(y)
print(model.predict(X))
```






