
## Python Pandas - Date Functionality

Extending the Time series, Date functionalities play major role in financial data analysis. 

While working with Date data, we will frequently come across the following − Generating sequence of dates Convert the 
date series to different frequencies 


### Create a Range of Dates 

Using the ``date.range()`` function by specifying the periods and the frequency,
we can create the date series. By default, the frequency of range is ``Days``.


```python
import pandas as pd 
print(pd.date_range('1/1/2018', periods=5) )
```

    DatetimeIndex(['2018-01-01', '2018-01-02', '2018-01-03', '2018-01-04',
                   '2018-01-05'],
                  dtype='datetime64[ns]', freq='D')



```python
### Change the Date Frequency
import pandas as pd 
print(pd.date_range('1/1/2018', periods=5,freq='M') )


   
```

    DatetimeIndex(['2018-01-31', '2018-02-28', '2018-03-31', '2018-04-30',
                   '2018-05-31'],
                  dtype='datetime64[ns]', freq='M')


### ``bdate_range`` 

``bdate_range()`` stands for business date ranges. 
Unlike ``date_range()``, it excludes Saturday and Sunday. 



```python
import pandas as pd 
print(pd.date_range('1/1/2018', periods=5))
    
```

    DatetimeIndex(['2011-01-01', '2011-01-02', '2011-01-03', '2011-01-04',
                   '2011-01-05'],
                  dtype='datetime64[ns]', freq='D')


Observe, after 3rd March, the date jumps to 6th march excluding 4th and 5th. Just check your calendar for the days. 

Convenience functions like ``date_range`` and ``bdate_range`` utilize a variety of frequency aliases.
    

The default frequency for ``date_range`` is a calendar day while the default for ``bdate_range`` is a business day.



```python
import pandas as pd 
start = pd.datetime(2018, 1, 1) 
end = pd.datetime(2018, 1, 8) 
print(pd.date_range(start, end))


```

    DatetimeIndex(['2018-01-01', '2018-01-02', '2018-01-03', '2018-01-04',
                   '2018-01-05', '2018-01-06', '2018-01-07', '2018-01-08'],
                  dtype='datetime64[ns]', freq='D')

