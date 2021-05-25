# Numpy: Python data types
#DataScience/Handbook/numpy

Variables in python are dynamically typed

Defining a python integer
`x=10000` actually generates a pointer to a C object:
```C
struct _longobject {
    long ob_refcnt;
    PyTypeObject *ob_type;
    size_t ob_size;
    long ob_digit[1];
};
```

So a Python variable is more than just an object with the bits of the variable, it has properties such as `size`, `type`, and `digit`. These properties allow Python to be dynamically typed – but also slow it down when too many are combined. That is where numpy arrays jump in: pointers to arrays of numbers of the same type.

Lists vs Arrays
![](Numpy%20Python%20data%20types/5D45ABE7-CDC6-4B1C-B274-D1E248E0E6CA.png)

Numpy arrays are _fixed type lists_

### Creating arrays from scratch
```python
np.full((3, 5), 3.14)
```





