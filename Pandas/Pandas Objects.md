# Pandas: Objects
#DataScience/Handbook/pandas


`pd.Series` are flexible generalizations of `numpy` arrays:
```python
population_dict = {'California': 38332521,
                   'Texas': 26448193,
                   'Texas': 19651127,
                   'Florida': 19552860,
                   'Illinois': 12882135}
population = pd.Series(population_dict)
population
#California    38332521
#Florida       19552860
#Illinois      12882135
#New York      19651127
#Texas         26448193
#dtype: int64
```

The index can be anything. A `pd.Series` is like a specialized dictionary.
```python
population['California':'Illinois']
#California    38332521
#Florida       19552860
#Illinois      12882135
#dtype: int64
```

Python set operations
```python
indA = pd.Index([1, 3, 5, 7, 9])
indB = pd.Index([2, 3, 5, 7, 11])

indA & indB  # intersection
# Out[36]:
# Int64Index([3, 5, 7], dtype=‘int64’)
indA | indB  # union
# Out[37]:
# Int64Index([1, 2, 3, 5, 7, 9, 11], dtype=‘int64’)
indA ^ indB  # symmetric difference
# Out[38]:
# Int64Index([1, 2, 9, 11], dtype=‘int64’)
```

