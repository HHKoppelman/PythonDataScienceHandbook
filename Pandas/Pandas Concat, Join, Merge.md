# Pandas: Concat, Join, Merge
#DataScience/Handbook/pandas


MultiIndexed DataFrame from concatenation:
```python
pd.concat([x, y], keys=['x', 'y'])
```


`pd.merge` can join dataframes in a smart way
![](Pandas%20Concat,%20Join,%20Merge/88026D9E-6844-4ABD-A023-5BCBE7BA237B.png)

Many-to-many joins
![](Pandas%20Concat,%20Join,%20Merge/CCF93E42-609C-4744-96BD-7C23EBD4024D.png)

Joins are merges on indices!
> For convenience, DataFrames implement the join() method, which performs a merge that defaults to joining on indices  

`inner`, `outer`, `left`, `right`
![](Pandas%20Concat,%20Join,%20Merge/A47386EC-9DA1-43DD-9446-7E74022AD59F.png)
