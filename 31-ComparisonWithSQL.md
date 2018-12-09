
Python Pandas - Comparison with SQL



Since many potential Pandas users have some familiarity with SQL, this page is meant to provide some examples of how various SQL operations can be performed using pandas.
import pandas as pd
url = 'https://raw.github.com/pandasdev/
pandas/master/pandas/tests/data/tips.csv'
tips=pd.read_csv(url)
print tips.head()
Its output is as follows −
    total_bill   tip      sex  smoker  day     time  size
0        16.99  1.01   Female      No  Sun  Dinner      2
1        10.34  1.66     Male      No  Sun  Dinner      3
2        21.01  3.50     Male      No  Sun  Dinner      3
3        23.68  3.31     Male      No  Sun  Dinner      2
4        24.59  3.61   Female      No  Sun  Dinner      4
SELECT
In SQL, selection is done using a comma-separated list of columns that you select (or a * to select all columns) −
SELECT total_bill, tip, smoker, time
FROM tips
LIMIT 5;
With Pandas, column selection is done by passing a list of column names to your DataFrame −
tips[['total_bill', 'tip', 'smoker', 'time']].head(5)
Let’s check the full program −
import pandas as pd

url = 'https://raw.github.com/pandasdev/
pandas/master/pandas/tests/data/tips.csv'
 
tips=pd.read_csv(url)
print tips[['total_bill', 'tip', 'smoker', 'time']].head(5)
Its output is as follows −
   total_bill   tip  smoker     time
0       16.99  1.01      No   Dinner
1       10.34  1.66      No   Dinner
2       21.01  3.50      No   Dinner
3       23.68  3.31      No   Dinner
4       24.59  3.61      No   Dinner
Calling the DataFrame without the list of column names will display all columns (akin to SQL’s *).
WHERE
Filtering in SQL is done via a WHERE clause.
  SELECT * FROM tips WHERE time = 'Dinner' LIMIT 5;
DataFrames can be filtered in multiple ways; the most intuitive of which is using Boolean indexing.
  tips[tips['time'] == 'Dinner'].head(5)
Let’s check the full program −
import pandas as pd

url = 'https://raw.github.com/pandasdev/
pandas/master/pandas/tests/data/tips.csv'

tips=pd.read_csv(url)
print tips[tips['time'] == 'Dinner'].head(5)
Its output is as follows −
   total_bill   tip      sex  smoker  day    time  size
0       16.99  1.01   Female     No   Sun  Dinner    2
1       10.34  1.66     Male     No   Sun  Dinner    3
2       21.01  3.50     Male     No   Sun  Dinner    3
3       23.68  3.31     Male     No   Sun  Dinner    2
4       24.59  3.61   Female     No   Sun  Dinner    4
The above statement passes a Series of True/False objects to the DataFrame, returning all rows with True.
GroupBy
This operation fetches the count of records in each group throughout a dataset. For instance, a query fetching us the number of tips left by sex −
SELECT sex, count(*)
FROM tips
GROUP BY sex;
The Pandas equivalent would be −
tips.groupby('sex').size()
Let’s check the full program −
import pandas as pd

url = 'https://raw.github.com/pandasdev/
pandas/master/pandas/tests/data/tips.csv'

tips=pd.read_csv(url)
print tips.groupby('sex').size()
Its output is as follows −
sex
Female   87
Male    157
dtype: int64
Top N rows
SQL returns the top n rows using LIMIT −
SELECT * FROM tips
LIMIT 5 ;
The Pandas equivalent would be −
tips.head(5)
Let’s check the full example −
import pandas as pd
url = 'https://raw.github.com/pandas-dev/pandas/master/pandas/tests/data/tips.csv'

tips=pd.read_csv(url)
tips = tips[['smoker', 'day', 'time']].head(5)
print tips
Its output is as follows −
   smoker   day     time
0      No   Sun   Dinner
1      No   Sun   Dinner
2      No   Sun   Dinner
3      No   Sun   Dinner
4      No   Sun   Dinner
These are the few basic operations we compared are, which we learnt, in the previous chapters of the Pandas Library.



