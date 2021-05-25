# Pandas: High-Performance
#DataScience/Handbook/pandas



In stead of masking, use: `df.query()`
In stead of applying operations, use `df.eval()`

Operations combing multiple dfs
```python
pd.eval('df1 + df2 + df3 + df4')
pd.eval('-df1 * df2 / (df3 + df4) - df5')
pd.eval('(df1 < 0.5) & (df2 < 0.5) | (df3 < df4)')
pd.eval('(df1 < 0.5) and (df2 < 0.5) or (df3 < df4)')
pd.eval('df2.T[0] + df3.iloc[1]')
```

But also operations on columns of a single df
```python
pd.eval('(df.A + df.B) / (df.C - 1)')
df.eval('(A + B) / (C - 1)') # Equivalent to operation above
df.eval('D = (A + B) / C', inplace=True)

#Using local variables:
column_mean = df.mean(1)
result1 = df['A'] + column_mean
result2 = df.eval('A + @column_mean')
```
> NB: this @ character is only supported by the `DataFrame.eval()` method, not by the `pandas.eval()` function, because the `pandas.eval()` function only has access to the one (Python) namespace.  


Masking a df using `df.query()`
```python 
df.query('A < 0.5 and B < 0.5')
# same as df[(df.A < 0.5) & (df.B < 0.5)]

# Also accepts local variables with @ flag
df.query('A < @Cmean and B < @Cmean')
```

Eval columns with space in name
```python
pd.eval('daily["dry day"] + daily["bad weather"]')
```