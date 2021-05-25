# Pandas: Time Series
#DataScience/Handbook/pandas

> Pandas was developed in the context of financial modeling  

Numpy has implemented a `datetime` `dtype` to work with dates and times. However, since this is based on a 64 bit format there are `2^64` options and thus either the resolution or the maximum time-span is limited:
![](Pandas%20Time%20Series/3E9FE27D-6690-4349-882D-2CBE8F0F45C7.png)

Creating a range of dates in `pandas`
```python
date = pd.to_datetime("4th of July, 2015")
date + pd.to_timedelta(np.arange(12), 'D')
```


Index by timestamps
```python
index = pd.DatetimeIndex([‘2014-07-04’, ‘2014-08-04’,
                          ‘2015-07-04’, ‘2015-08-04’])
data = pd.Series([0, 1, 2, 3], index=index)
print(data['2014-07-04':'2015-07-04'])
print(data['2015'])
```


Three different pandas date and time types
* `Timestamp` or the associated `DatetimeIndex`
* `Period` or `PeriodIndex`
* `Timdedelta` or `TimedeltaIndex`


Creating ranges of dates
```python
pd.date_range('2015-07-03', '2015-07-10')
pd.date_range('2015-07-03', periods=8)
pd.date_range('2015-07-03', periods=8, freq='H')
```


Formats:
![](Pandas%20Time%20Series/3DC2F363-74F0-4246-99A0-EEB0728D45F2.png)
> The monthly, quarterly, and annual frequencies are all marked at the end of the specified period. By adding an S suffix to any of these, they instead will be marked at the beginning:  
![](Pandas%20Time%20Series/E2DABC91-EEAD-48E2-AF75-438DE58ABF29.png)
> Additionally, you can change the month used to mark any quarterly or annual code by adding a three-letter month code as a suffix:  
![](Pandas%20Time%20Series/F246AA74-7004-46D2-A56B-D6AFE0302AB8.png)
> In the same way, the split-point of the weekly frequency can be modified by adding a three-letter weekday code:  
* `W-SUN`, `W-MON`, `W-TUE`, `W-WED`, etc.

```python
# Business annuals starting in February
pd.date_range(0, periods=9, freq="BAS-FEB")
# Output corresponds to first business day of the business year starting in February
```







