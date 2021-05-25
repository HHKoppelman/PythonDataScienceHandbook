# Pandas: Indexing & Selection
#DataScience/Handbook/pandas


`loc` vs `iloc`
One is implicit, the other is not:
```python
data = pd.Series(['a', 'b', 'c'], index=[1, 3, 5])
data.loc[1]
# 'a'
data.iloc[1]
# 'b'
```

`ix` is a hybrid of both for `pd.DataFrame`
```python
data.ix[:3, :'pop']
```


Masking and indexing in `df.loc`
```python
data.loc[data.density > 100, [‘pop’, ‘density’]]
```
