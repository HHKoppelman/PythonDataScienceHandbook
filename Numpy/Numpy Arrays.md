# Numpy: Arrays
#DataScience/Handbook/numpy


### Attributes
```python
x = np.linspace()
x.dim
x.shape
x.size
```


Reverse stacking: splitting
```python
x = [1, 2, 3, 99, 99, 3, 2, 1]
x1, x2, x3 = np.split(x, [3, 5])
print(x1, x2, x3)
# [1 2 3] [99 99] [3 2 1]
```