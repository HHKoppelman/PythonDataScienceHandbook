# Numpy: Broadcasting
#DataScience/Handbook/numpy


```python 
a = np.arange(3)
b = np.arange(3)[:, np.newaxis]

print(a)
print(b)
# [0 1 2]
# [[0]
# [1]
# [2]]
```

```python
a + b
# array([[0, 1, 2],
#       [1, 2, 3],
#       [2, 3, 4]])
```

```python
M = np.ones((3, 2))
a = np.arange(3)
np.logaddexp(M, a[:, np.newaxis])
# Out[16]: array([[ 1.31326169,  1.31326169],
#      [ 1.69314718,  1.69314718],
#      [ 2.31326169,  2.31326169]])
```