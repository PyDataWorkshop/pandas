
Python Pandas - IO Tools

The Pandas I/O API is a set of top level reader functions accessed like pd.read_csv() that generally return a Pandas object.
The two workhorse functions for reading text files (or the flat files) are read_csv() and read_table(). They both use the same parsing code to intelligently convert tabular data into a DataFrame object −
pandas.read_csv(filepath_or_buffer, sep=',', delimiter=None, header='infer',
names=None, index_col=None, usecols=None

pandas.read_csv(filepath_or_buffer, sep='\t', delimiter=None, header='infer',
names=None, index_col=None, usecols=None
Here is how the csv file data looks like −
S.No,Name,Age,City,Salary
1,Tom,28,Toronto,20000
2,Lee,32,HongKong,3000
3,Steven,43,Bay Area,8300
4,Ram,38,Hyderabad,3900
Save this data as temp.csv and conduct operations on it.
S.No,Name,Age,City,Salary
1,Tom,28,Toronto,20000
2,Lee,32,HongKong,3000
3,Steven,43,Bay Area,8300
4,Ram,38,Hyderabad,3900
Save this data as temp.csv and conduct operations on it.
read.csv
read.csv reads data from the csv files and creates a DataFrame object.
import pandas as pd
df=pd.read_csv("temp.csv")
print df
Its output is as follows −
   S.No     Name   Age       City   Salary
0     1      Tom    28    Toronto    20000
1     2      Lee    32   HongKong     3000
2     3   Steven    43   Bay Area     8300
3     4      Ram    38  Hyderabad     3900
custom index
This specifies a column in the csv file to customize the index using index_col.
import pandas as pd

df=pd.read_csv("temp.csv",index_col=['S.No'])
print df
Its output is as follows −
S.No   Name   Age       City   Salary
1       Tom    28    Toronto    20000
2       Lee    32   HongKong     3000
3    Steven    43   Bay Area     8300
4       Ram    38  Hyderabad     3900
Converters
dtype of the columns can be passed as a dict.
import pandas as pd

df = pd.read_csv("temp.csv", dtype={'Salary': np.float64})
print df.dtypes
Its output is as follows −
S.No       int64
Name      object
Age        int64
City      object
Salary   float64
dtype: object
By default, the dtype of the Salary column is int, but the result shows it as float because we have explicitly casted the type.
Thus, the data looks like float −
  S.No   Name   Age      City    Salary
0   1     Tom   28    Toronto   20000.0
1   2     Lee   32   HongKong    3000.0
2   3  Steven   43   Bay Area    8300.0
3   4     Ram   38  Hyderabad    3900.0
header_names
Specify the names of the header using the names argument.
import pandas as pd
 
df=pd.read_csv("temp.csv", names=['a', 'b', 'c','d','e'])
print df
Its output is as follows −
       a        b    c           d        e
0   S.No     Name   Age       City   Salary
1      1      Tom   28     Toronto    20000
2      2      Lee   32    HongKong     3000
3      3   Steven   43    Bay Area     8300
4      4      Ram   38   Hyderabad     3900
Observe, the header names are appended with the custom names, but the header in the file has not been eliminated. Now, we use the header argument to remove that.
If the header is in a row other than the first, pass the row number to header. This will skip the preceding rows.
import pandas as pd 

df=pd.read_csv("temp.csv",names=['a','b','c','d','e'],header=0)
print df
Its output is as follows −
      a        b    c           d        e
0  S.No     Name   Age       City   Salary
1     1      Tom   28     Toronto    20000
2     2      Lee   32    HongKong     3000
3     3   Steven   43    Bay Area     8300
4     4      Ram   38   Hyderabad     3900
skiprows
skiprows skips the number of rows specified.
import pandas as pd

df=pd.read_csv("temp.csv", skiprows=2)
print df
Its output is as follows −
    2      Lee   32    HongKong   3000
0   3   Steven   43    Bay Area   8300
1   4      Ram   38   Hyderabad   3900


