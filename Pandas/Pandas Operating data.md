# Pandas: Operating data
#DataScience/Handbook/pandas


Any of the `numpy` Ufuncs can be applied to data frames
```python
np.log(df)
```


Pandas can deal with incomplete data
```python
area = pd.Series({'Alaska': 1723337, 'Texas': 695662,
                  'California': 423967}, name='area')
population = pd.Series({'California': 38332521, 'Texas': 26448193,
                        'New York': 19651127}, name='population')

population / area
# Alaska              NaN
# California    90.413926
# New York            NaN
# Texas         38.018740
# dtype: float64
```

Union of indexes:
```python
area.index | population.index
# Index(['Alaska', 'California', 'New York', 'Texas'], dtype='object')
```


Adding data frames and filling with mean
```python
fill = A.stack().mean()
A.add(B, fill_value=fill)
```


`numpy` only has a float `NaN`
Pandas as of version 0.24 has an integer NaN

