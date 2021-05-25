# Pandas: Pivot Tables
#DataScience/Handbook/pandas

> pivot tables are essentially a multidimensional version of GroupBy aggregation  


```python
# These have the same outputs, latter is simpler to understand.
titanic.groupby(['sex', 'class'])['survived'].aggregate('mean').unstack()
titanic.pivot_table('survived', index='sex', columns='class')
```


Advanced pivot
```python
age = pd.cut(titanic['age'], [0, 18, 80])
titanic.pivot_table('survived', ['sex', age], 'class')
```
![](Pandas%20Pivot%20Tables/AED2BFD4-5CCD-4CAA-B381-E49D89DC02A8.png)

Even more advanced: `pd.cut` on rows and `pd.qcut` on fare
```python
fare = pd.qcut(titanic['fare'], 2)
titanic.pivot_table('survived', ['sex', age], [fare, 'class'])
```
![](Pandas%20Pivot%20Tables/C3C85A70-ACBC-4A73-89D1-A3683B470EAC.png)

```python
titanic.pivot_table(index='sex', columns='class',
                    aggfunc={'survived':sum, 'fare':'mean'})
```
![](Pandas%20Pivot%20Tables/E79F164E-5F44-43AF-9484-CF25A6ECDE84.png)

```python
titanic.pivot_table('survived', index='sex', columns='class', margins=True, margins_name='Tot')
```
Adds a summary row and column

See [Pivot Tables | Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/03.09-pivot-tables.html)
For some really cool example on birth rate analysis and pandas date time operations!
