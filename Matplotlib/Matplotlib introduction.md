# Matplotlib: introduction
#DataScience/Handbook/matplotlib

Get supported filetypes
```python
fig.canvas.get_supported_filetypes()
# {'eps': 'Encapsulated Postscript',
#  'jpeg': 'Joint Photographic Experts Group',
#  'jpg': 'Joint Photographic Experts Group',
#  'pdf': 'Portable Document Format',
#  'pgf': 'PGF code for LaTeX',
#  'png': 'Portable Network Graphics',
#  'ps': 'Postscript',
#  'raw': 'Raw RGBA bitmap',
#  'rgba': 'Raw RGBA bitmap',
#  'svg': 'Scalable Vector Graphics',
#  'svgz': 'Scalable Vector Graphics',
#  'tif': 'Tagged Image File Format',
#  'tiff': 'Tagged Image File Format'}
```

Setting aspect ratios
```python
plt.axis('tight');
plt.axis('equal');
```

`plot >> scatter`
`plt.plot` can be noticeably more efficient than `plt.scatter`
> The reason is that `plt.scatter` has the capability to render a different size and/or color for each point, so the renderer must do the extra work of constructing each point individually. In `plt.plot`, on the other hand, the points are always essentially clones of each other, so the work of determining the appearance of the points is done only once for the entire set of data.  


Advanced legend manipulation
```python
x = np.linspace(0, 10, 1000)
y = np.sin(x[:, np.newaxis] + np.pi * np.arange(0, 2, 0.5))
lines = plt.plot(x, y)

/# lines is a list of plt.Line2D instances/
plt.legend(lines[:2], ['first', 'second']);
```


Multiple legends
```python
fig, ax = plt.subplots()

lines = []
styles = ['-', '--', '-.', ':']
x = np.linspace(0, 10, 1000)

for i in range(4):
    lines += ax.plot(x, np.sin(x - i * np.pi / 2),
                     styles[i], color='black')
ax.axis('equal')

# specify the lines and labels of the first legend
ax.legend(lines[:2], ['line A', 'line B'],
          loc='upper right', frameon=False)

# Create the second legend and add the artist manually.
from matplotlib.legend import Legend
leg = Legend(ax, lines[2:], ['line C', 'line D'],
             loc='lower right', frameon=False)
ax.add_artist(leg);
```

Add arrows on top of colorbar
```python
plt.colorbar(extend='both')
```

Colorbar clim
```python
plt.clim(-1, 1);
```
