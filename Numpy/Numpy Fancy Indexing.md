# Numpy: Fancy Indexing
#DataScience/Handbook/numpy

Quick binning
```python
np.random.seed(42)
x = np.random.randn(100)

/# compute a histogram by hand/
bins = np.linspace(-5, 5, 20)
counts = np.zeros_like(bins)

/# find the appropriate bin for each x/
I = np.searchsorted(bins, x)

/# add 1 to each of these bins/
np.add.at(counts, I, 1)
```