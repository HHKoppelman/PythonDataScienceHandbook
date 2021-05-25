# IPython: errors and debugging
#DataScience/Handbook/IPython

Three debugging modes:
```python
%xmode Context # default
%xmode Plain
%xmode Verbose
```

Debugging tools:
```python
%debug
```

Enters the `ipbd` debugging mode in which one can print outputs and quit. For example:
``` python
> <ipython-input-1-d849e34d61fb>(2)func1()
      1 def func1(a, b):
——> 2     return a / b
      3 

ipdb> up
> <ipython-input-1-d849e34d61fb>(7)func2()
      5     a = x
      6     b = x - 1
——> 7     return func1(a, b)

ipdb> print(x)
1
ipdb> up
> <ipython-input-6-b2e110f6fc8f>(1)<module>()
——> 1 func2(1)

ipdb> down
> <ipython-input-1-d849e34d61fb>(7)func2()
      5     a = x
      6     b = x - 1
——> 7     return func1(a, b)

ipdb> quit
```

To automatically launch the debugger:
```python
%xmode Plain
%pdb on
func2(1)
```

Some debugging commands:
**Command**		**Description**
`list`				Show the current location in the file
`h(elp)`			Show a list of commands, or find help on a specific command
`q(uit)`			Quit the debugger and the program
`c(ontinue)`		Quit the debugger, continue in the program
`n(ext)`			Go to the next step of the program
`<enter>	`		Repeat the previous command
`p(rint)`			Print variables
`s(tep)`			Step into a subroutine
`r(eturn)`			Return out of a subroutine
