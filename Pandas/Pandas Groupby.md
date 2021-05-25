# Pandas: Groupby
#DataScience/Handbook/pandas


Groupby: split, apply, combine
![](Numpy%20Python%20data%20types/unknown.png)

Groupby and describe
```python
planets.groupby('method')['year'].describe()
```


Groupby and filter
```python
def filter_func(x):
    return x['data2'].std() > 4
```
![](Numpy%20Python%20data%20types/EF2C1891-2292-4308-AC4E-C8018EBB10BA.png)

Subtracting group-wise mean
```python
df.groupby('key').transform(lambda x: x - x.mean())
```
Same:
```python
def center(x):
    x = x-x.mean() 
    return x
df.groupby('key').transform(center)
```

Groupby & Aggregate
```python
df.groupby('key').aggregate({'data1': 'min',
                             'data2': 'max'})
```

Groupby and mapping
```python
df2 = df.set_index('key')
mapping = {'A': 'vowel', 'B': 'consonant', 'C': 'consonant'}
df2.groupby(mapping).sum()
```
![](Numpy%20Python%20data%20types/C730F92F-99A9-4A00-B3A4-E761A38726F0.png)

```python
df2.groupby(str.lower).mean()
```
![](Numpy%20Python%20data%20types/EFC021CF-E0FF-4CF6-A29C-EEFD93385A6B.png)

```python
df2.groupby([str.lower, mapping]).mean()
```
![](Numpy%20Python%20data%20types/D92EE851-5C95-4A9B-B1D7-42F462637F6D.png)


```python
decade = 10 * (planets['year'] // 10)
decade = decade.astype(str) + 's'
decade.name = 'decade'
planets.groupby(['method', decade])['number'].sum().unstack().fillna(0)
```
![](Numpy%20Python%20data%20types/A52D3FA9-A19C-411F-8C21-4170E06705D5.png)