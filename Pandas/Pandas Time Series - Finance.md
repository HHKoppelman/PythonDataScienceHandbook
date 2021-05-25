# Pandas: Time Series - Finance
#DataScience/Handbook/pandas

> Pandas was developed in the context of financial modeling  

`conda install pandas-datareader`

AAPL share prices from yahoo:
```python
aapl = data.DataReader('AAPL', start='2015', end=None,
                       data_source='yahoo')
```


> `resample()` is fundamentally a data aggregation, while `asfreq()` is fundamentally a data selection.  

Three options to fill nans
```python
fig, ax = plt.subplots(2, sharex=True)
data = aapl.iloc[:10]

data.asfreq('D').plot(ax=ax[0], marker='o')

data.asfreq('D', method='bfill').plot(ax=ax[1], style='-o')
data.asfreq('D', method='ffill').plot(ax=ax[1], style='--o')


(data.asfreq('D', method='bfill')/2 + data.asfreq('D', method='ffill')/2).plot(ax=ax[1], style='-o')
ax[1].legend(["back-fill", "forward-fill", 'mean f/b fill']);
```
![](Numpy%20Python%20data%20types/unknown.png)

Shifting the data: `shift` vs `tshift`
The former shifts the data and the latter shifts the time index
![](Numpy%20Python%20data%20types/8C4D991A-6A4A-4A3F-A41E-2647958265B4.png)

Using shifts to calculate the yearly ROI
```python
ROI = 100 * (aapl.tshift(-365) / aapl - 1)
ROI.plot()
plt.ylabel('% Return on Investment');
# Is this really the ROI though?
# Fine, the one-year ROI for investing in Apple stock.
```
![](Numpy%20Python%20data%20types/unknown%202.png)
-> Which has been pretty good for Apple!

Rolling windows:
```python
rolling = aapl.rolling(365, center=True)
plt.plot(rolling.mean())
```
Various windows are available - and custom methods are possible.

For example: 50 day rolling mean of a 10 day Gaussian cut-off
```python
daily.rolling(50, center=True, win_type='gaussian').sum(std=10)
```


