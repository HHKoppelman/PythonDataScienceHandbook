# Pandas: Hierarchical Indexing
#DataScience/Handbook/pandas

Multi-dimensional data
Actually, the 3D and 4D versions of a DataFrame exist: `pd.Panel` and `pd.Panel4D`

```python
df = pd.DataFrame(np.random.rand(4, 2),
                  index=[['a', 'a', 'b', 'b'], [1, 2, 1, 2]],
                  columns=['data1', 'data2'])
df
```


`MultiIndex` level names
```python
pop.index.names = ['state', 'year']
pop
# Out[18]:
# state       year
# California  2000    33871648
#             2010    37253956
# New York    2000    18976457
#             2010    19378102
# Texas       2000    20851820
#             2010    25145561
# dtype: int64
```

```python
# hierarchical indices and columns
index = pd.MultiIndex.from_product([[2013, 2014], [1, 2]],
                                   names=['year', 'visit'])
columns = pd.MultiIndex.from_product([['Bob', 'Guido', 'Sue'], ['HR', 'Temp']],
                                     names=['subject', 'type'])

# mock some data
data = np.round(np.random.randn(4, 6), 1)
data[:, ::2] *= 10
data += 37

# create the DataFrame
health_data = pd.DataFrame(data, index=index, columns=columns)
health_data
# 			subject	Bob				Guido			Sue
#			type	HR		Temp	HR		Temp	HR		Temp
# year	visit						
# 2013		1	31.0	38.7	32.0	36.7	35.0	37.2
#	 			2	44.0	37.7	50.0	35.0	29.0	36.7
# 2014		1	30.0	37.4	39.0	37.8	61.0	36.9
# 				2	47.0	37.8	48.0	37.3	51.0	36.5

```

