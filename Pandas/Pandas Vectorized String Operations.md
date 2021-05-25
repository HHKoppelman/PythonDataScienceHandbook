# Pandas: Vectorized String Operations
#DataScience/Handbook/pandas


All the following operations are possible on `df.str`
`len()`     `lower()`      `translate()`  `islower()`  
`ljust()`   `upper()`      `startswith()` `isupper()`  
`rjust()`   `find()`       `endswith()`   `isnumeric()`  
`center()`  `rfind()`      `isalnum()`    `isdecimal()`  
`zfill()`   `index()`      `isalpha()`    `split()`  
`strip()`   `rindex()`     `isdigit()`    `rsplit()`  
`rstrip()`  `capitalize()` `isspace()`    `partition()`  
`lstrip()`  `swapcase()`   `istitle()`    `rpartition()`  

And some methods use regular expressions

Split and get last item:
```python
monte.str.split().str.get(-1)
```