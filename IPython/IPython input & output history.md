# IPython: input & output history
#DataScience/Handbook/IPython


Accessing `In` and `Out` from cells
```python
In [4]: *print*(In)
[‘’, ‘import math’, ‘math.sin(2)’, ‘math.cos(2)’, ‘print(In)’]

In [5]: Out
Out[5]: {2: 0.9092974268256817, 3: -0.4161468365471424}
```

```python
In [6]: *print*(In[1])
*import* *math*
```



Accessing previous `Out`:
```python
In [9]: *print*(_) # Last out
1.0

In [10]: print(__) # Second to last
-0.4161468365471424

In [11]: print(___) # Third to last
0.9092974268256817
```

