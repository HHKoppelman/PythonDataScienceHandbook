# Numpy: Sorting Arrays
#DataScience/Handbook/numpy


```python
def bogosort(x):
    while np.any(x[:-1] > x[1:]):
        np.random.shuffle(x)
    return x
```
Haha..

Finding just the three smallest numbers
```python
x = np.array([7, 2, 3, 1, 6, 5, 4])
np.partition(x, 3)
```