# IPython: help and documentation
#DataScience/Handbook/IPython

access source code: `??`

```python
In [8]: square??
Type:        function
String form: <function square at 0x103713cb0>
Definition:  square(a)
Source:
def square(a):
    "Return the square of a"
    return a ** 2
```


Wildcard matching: `*`
```python
In [10]: *Warning?
BytesWarning                  RuntimeWarning
DeprecationWarning            SyntaxWarning
FutureWarning                 UnicodeWarning
ImportWarning                 UserWarning
PendingDeprecationWarning     Warning
ResourceWarning
```


```python
In [10]: str.*find*?
str.find
str.rfind
```

