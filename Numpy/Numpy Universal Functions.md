# Numpy: Universal Functions
#DataScience/Handbook/numpy


Optimized calculations through _vectorized operations_

Any operation applied on vectors:
```python
x = np.arange(4)
print(“x     =“, x)
print(“x + 5 =“, x + 5)
print(“x - 5 =“, x - 5)
print(“x * 2 =“, x * 2)
print(“x / 2 =“, x / 2)
print(“x // 2 =“, x // 2)  /# floor division/
```



Exponent minus one, or log plus one are also available.
```python
x = [0, 0.001, 0.01, 0.1]
print(“exp(x) - 1 =“, np.expm1(x))
print(“log(1 + x) =“, np.log1p(x))
```

### Advanced Ufunc Features

Specifying the output:
```python
x = np.arange(5)
y = np.empty(5)
np.multiply(x, 10, out=y)
print(y)
```


This can save memory:
```python 
y = np.zeros(10)
np.power(2, x, out=y[::2])
print(y)
```
The operation above directly stores the output in `y`, in stead of storing it first in an intermediate vector. Consider the operation `y[::2] = 2 ** x` which would have required more memory.

### Aggregates
```python
x = np.arange(1, 6)
np.add.reduce(x)
# 15
np.add.accumulate(x)
# array([ 1,  3,  6, 10, 15])
```

See also `ufunc.at` and `ufunc.reduceat`

```python
x = np.zeros(10)
i = [2, 3, 3, 4, 4, 4]
np.add.at(x, i, 1)
print(x)
# [ 0.  0.  1.  2.  3.  0.  0.  0.  0.  0.]
```


### Outer products
```python
x = np.arange(1, 6)
np.multiply.outer(x, x)
```