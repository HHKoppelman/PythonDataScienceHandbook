# Pandas: DataFrame methods
#DataScience/Handbook/pandas




Check if monotonic
```python
print(aapl.is_monotonic)
print(aapl.is_monotonic_decreasing)
print(aapl.is_monotonic_increasing)
```
Find n largest or smallest
```python
aapl.nlargest(4)
aapl.nsmallest(4)
```


Some other, perhaps useful methods:
```python

# Exponential weighted (EW) functions
print(aapl.ewm.__doc__)

# Factorizing strings
print(aapl.factorize.__doc__)
['a','b'] -> [0,1]

# Percentage change:
aapl.pct_change()

# Unbiased standard error of mean
print(aapl.sem.__doc__)

# Conversion between time-zones
print(aapl.tz_convert.__doc__)

# Cross-section:
print(aapl.xs.__doc__)

d = {'num_legs': [4, 4, 2, 2],
     'num_wings': [0, 0, 2, 2],
     'class': ['mammal', 'mammal', 'mammal', 'bird'],
     'animal': ['cat', 'dog', 'bat', 'penguin'],
     'locomotion': ['walks', 'walks', 'flies', 'walks']}
df = pd.DataFrame(data=d)
df = df.set_index(['class', 'animal', 'locomotion'])
df

df.xs('mammal') # -> shows only the mammals, not the birds

```