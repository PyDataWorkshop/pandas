
Python Pandas - Basic Functionality

Advertisements


 Previous Page 
Next Page   


By now, we learnt about the three Pandas DataStructures and how to create them. We will majorly focus on the DataFrame objects because of its importance in the real time data processing and also discuss a few other DataStructures.
Series Basic Functionality
S.No.
Attribute or Method
Description
1
axes
Returns a list of the row axis labels.
2
dtype
Returns the dtype of the object.
3
empty
Returns True if series is empty.
4
ndim
Returns the number of dimensions of the underlying data, by definition 1.
5
size
Returns the number of elements in the underlying data.
6
values
Returns the Series as ndarray.
7
head()
Returns the first n rows.
8
tail()
Returns the last n rows.
Let us now create a Series and see all the above tabulated attributes operation.
Example
import pandas as pd
import numpy as np

#Create a series with 100 random numbers
s = pd.Series(np.random.randn(4))
print s
Its output is as follows −
0   0.967853
1  -0.148368
2  -1.395906
3  -1.758394
dtype: float64
axes
Returns the list of the labels of the series.
import pandas as pd
import numpy as np

#Create a series with 100 random numbers
s = pd.Series(np.random.randn(4))
print ("The axes are:")
print s.axes
Its output is as follows −
The axes are:
[RangeIndex(start=0, stop=4, step=1)]
The above result is a compact format of a list of values from 0 to 5, i.e., [0,1,2,3,4].
empty
Returns the Boolean value saying whether the Object is empty or not. True indicates that the object is empty.
import pandas as pd
import numpy as np

#Create a series with 100 random numbers
s = pd.Series(np.random.randn(4))
print ("Is the Object empty?")
print s.empty
Its output is as follows −
Is the Object empty?
False
ndim
Returns the number of dimensions of the object. By definition, a Series is a 1D data structure, so it returns 
import pandas as pd
import numpy as np

#Create a series with 4 random numbers
s = pd.Series(np.random.randn(4))
print s

print ("The dimensions of the object:")
print s.ndim
Its output is as follows −
0   0.175898
1   0.166197
2  -0.609712
3  -1.377000
dtype: float64

The dimensions of the object:
1
size
Returns the size(length) of the series.
import pandas as pd
import numpy as np

#Create a series with 4 random numbers
s = pd.Series(np.random.randn(2))
print s
print ("The size of the object:")
print s.size
Its output is as follows −
0   3.078058
1  -1.207803
dtype: float64

The size of the object:
2
values
Returns the actual data in the series as an array.
import pandas as pd
import numpy as np

#Create a series with 4 random numbers
s = pd.Series(np.random.randn(4))
print s

print ("The actual data series is:")
print s.values
Its output is as follows −
0   1.787373
1  -0.605159
2   0.180477
3  -0.140922
dtype: float64

The actual data series is:
[ 1.78737302 -0.60515881 0.18047664 -0.1409218 ]
Head & Tail
To view a small sample of a Series or the DataFrame object, use the head() and the tail() methods.
head() returns the first n rows(observe the index values). The default number of elements to display is five, but you may pass a custom number.
import pandas as pd
import numpy as np

#Create a series with 4 random numbers
s = pd.Series(np.random.randn(4))
print ("The original series is:")
print s

print ("The first two rows of the data series:")
print s.head(2)
Its output is as follows −
The original series is:
0   0.720876
1  -0.765898
2   0.479221
3  -0.139547
dtype: float64

The first two rows of the data series:
0   0.720876
1  -0.765898
dtype: float64
tail() returns the last n rows(observe the index values). The default number of elements to display is five, but you may pass a custom number.
import pandas as pd
import numpy as np

#Create a series with 4 random numbers
s = pd.Series(np.random.randn(4))
print ("The original series is:")
print s

print ("The last two rows of the data series:")
print s.tail(2)
Its output is as follows −
The original series is:
0 -0.655091
1 -0.881407
2 -0.608592
3 -2.341413
dtype: float64

The last two rows of the data series:
2 -0.608592
3 -2.341413
dtype: float64
DataFrame Basic Functionality
Let us now understand what DataFrame Basic Functionality is. The following tables lists down the important attributes or methods that help in DataFrame Basic Functionality.
S.No.
Attribute or Method
Description
1
T
Transposes rows and columns.
2
axes
Returns a list with the row axis labels and column axis labels as the only members.
3
dtypes
Returns the dtypes in this object.
4
empty
True if NDFrame is entirely empty [no items]; if any of the axes are of length 0.
5
ndim
Number of axes / array dimensions.
6
shape
Returns a tuple representing the dimensionality of the DataFrame.
7
size
Number of elements in the NDFrame.
8
values
Numpy representation of NDFrame.
9
head()
Returns the first n rows.
10
tail()
Returns last n rows.
Let us now create a DataFrame and see all how the above mentioned attributes operate.
Example
import pandas as pd
import numpy as np

#Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]),
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}

#Create a DataFrame
df = pd.DataFrame(d)
print ("Our data series is:")
print df
Its output is as follows −
Our data series is:
    Age   Name    Rating
0   25    Tom     4.23
1   26    James   3.24
2   25    Ricky   3.98
3   23    Vin     2.56
4   30    Steve   3.20
5   29    Smith   4.60
6   23    Jack    3.80
T (Transpose)
Returns the transpose of the DataFrame. The rows and columns will interchange.
import pandas as pd
import numpy as np
 
# Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]),
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}

# Create a DataFrame
df = pd.DataFrame(d)
print ("The transpose of the data series is:")
print df.T
Its output is as follows −
The transpose of the data series is:
         0     1       2      3      4      5       6
Age      25    26      25     23     30     29      23
Name     Tom   James   Ricky  Vin    Steve  Smith   Jack
Rating   4.23  3.24    3.98   2.56   3.2    4.6     3.8
axes
Returns the list of row axis labels and column axis labels.
import pandas as pd
import numpy as np

#Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]),
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}

#Create a DataFrame
df = pd.DataFrame(d)
print ("Row axis labels and column axis labels are:")
print df.axes
Its output is as follows −
Row axis labels and column axis labels are:

[RangeIndex(start=0, stop=7, step=1), Index([u'Age', u'Name', u'Rating'],
dtype='object')]
dtypes
Returns the data type of each column.
import pandas as pd
import numpy as np

#Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]),
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}

#Create a DataFrame
df = pd.DataFrame(d)
print ("The data types of each column are:")
print df.dtypes
Its output is as follows −
The data types of each column are:
Age     int64
Name    object
Rating  float64
dtype: object
empty
Returns the Boolean value saying whether the Object is empty or not; True indicates that the object is empty.
import pandas as pd
import numpy as np
 
#Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]),
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}
 
#Create a DataFrame
df = pd.DataFrame(d)
print ("Is the object empty?")
print df.empty
Its output is as follows −
Is the object empty?
False
ndim
Returns the number of dimensions of the object. By definition, DataFrame is a 2D object.
import pandas as pd
import numpy as np

#Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]),
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}

#Create a DataFrame
df = pd.DataFrame(d)
print ("Our object is:")
print df
print ("The dimension of the object is:")
print df.ndim
Its output is as follows −
Our object is:
      Age    Name     Rating
0     25     Tom      4.23
1     26     James    3.24
2     25     Ricky    3.98
3     23     Vin      2.56
4     30     Steve    3.20
5     29     Smith    4.60
6     23     Jack     3.80

The dimension of the object is:
2
shape
Returns a tuple representing the dimensionality of the DataFrame. Tuple (a,b), where a represents the number of rows and b represents the number of columns.
import pandas as pd
import numpy as np
 
#Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]),
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}
 
#Create a DataFrame
df = pd.DataFrame(d)
print ("Our object is:")
print df
print ("The shape of the object is:")
print df.shape
Its output is as follows −
Our object is:
   Age   Name    Rating
0  25    Tom     4.23
1  26    James   3.24
2  25    Ricky   3.98
3  23    Vin     2.56
4  30    Steve   3.20
5  29    Smith   4.60
6  23    Jack    3.80

The shape of the object is:
(7, 3)
size
Returns the number of elements in the DataFrame.
import pandas as pd
import numpy as np
 
#Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]),
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}
 
#Create a DataFrame
df = pd.DataFrame(d)
print ("Our object is:")
print df
print ("The total number of elements in our object is:")
print df.size
Its output is as follows −
Our object is:
    Age   Name    Rating
0   25    Tom     4.23
1   26    James   3.24
2   25    Ricky   3.98
3   23    Vin     2.56
4   30    Steve   3.20
5   29    Smith   4.60
6   23    Jack    3.80

The total number of elements in our object is:
21
values
Returns the actual data in the DataFrame as an NDarray.
import pandas as pd
import numpy as np
 
#Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]),
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}
 
#Create a DataFrame
df = pd.DataFrame(d)
print ("Our object is:")
print df
print ("The actual data in our data frame is:")
print df.values
Its output is as follows −
Our object is:
    Age   Name    Rating
0   25    Tom     4.23
1   26    James   3.24
2   25    Ricky   3.98
3   23    Vin     2.56
4   30    Steve   3.20
5   29    Smith   4.60
6   23    Jack    3.80
The actual data in our data frame is:
[[25 'Tom' 4.23]
[26 'James' 3.24]
[25 'Ricky' 3.98]
[23 'Vin' 2.56]
[30 'Steve' 3.2]
[29 'Smith' 4.6]
[23 'Jack' 3.8]]
Head & Tail
To view a small sample of a DataFrame object, use the head() and tail() methods. head() returns the first n rows (observe the index values). The default number of elements to display is five, but you may pass a custom number.
import pandas as pd
import numpy as np
 
#Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]),
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}

#Create a DataFrame
df = pd.DataFrame(d)
print ("Our data frame is:")
print df
print ("The first two rows of the data frame is:")
print df.head(2)
Its output is as follows −
Our data frame is:
    Age   Name    Rating
0   25    Tom     4.23
1   26    James   3.24
2   25    Ricky   3.98
3   23    Vin     2.56
4   30    Steve   3.20
5   29    Smith   4.60
6   23    Jack    3.80

The first two rows of the data frame is:
   Age   Name   Rating
0  25    Tom    4.23
1  26    James  3.24
tail() returns the last n rows (observe the index values). The default number of elements to display is five, but you may pass a custom number.
import pandas as pd
import numpy as np

#Create a Dictionary of series
d = {'Name':pd.Series(['Tom','James','Ricky','Vin','Steve','Smith','Jack']),
   'Age':pd.Series([25,26,25,23,30,29,23]), 
   'Rating':pd.Series([4.23,3.24,3.98,2.56,3.20,4.6,3.8])}
 
#Create a DataFrame
df = pd.DataFrame(d)
print ("Our data frame is:")
print df
print ("The last two rows of the data frame is:")
print df.tail(2)
Its output is as follows −
Our data frame is:
    Age   Name    Rating
0   25    Tom     4.23
1   26    James   3.24
2   25    Ricky   3.98
3   23    Vin     2.56
4   30    Steve   3.20
5   29    Smith   4.60
6   23    Jack    3.80

The last two rows of the data frame is:
    Age   Name    Rating
5   29    Smith    4.6
6   23    Jack     3.8


