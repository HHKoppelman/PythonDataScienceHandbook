# Numpy: Comparison, Masks, Boolean Logic
#DataScience/Handbook/numpy


```python
# how many values less than 6?
np.count_nonzero(x < 6)
```
::Is faster than `(x<6).sum()`::