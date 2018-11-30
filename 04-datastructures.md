
Who is Who
Introduction to Data Structures



Pandas deals with the following three data structures −
1. Series
2. DataFrame
3. Panel

These data structures are built on top of Numpy array, which means they are fast.

#### Dimension & Description

The best way to think of these data structures is that the higher dimensional data structure is a container of its lower dimensional data structure. For example, DataFrame is a container of Series, Panel is a container of DataFrame.

#### Data Structure

Structure Dimensions Description
Series 1 1D labeled homogeneous array, sizeimmutable.
Data Frames 2 General 2D labeled, size-mutable tabular structure with potentially heterogeneously typed columns.
Panel 3 General 3D labeled, size-mutable array.

Building and handling two or more dimensional arrays is a tedious task, burden is placed on the user to consider the orientation of the data set when writing functions. But using Pandas data structures, the mental effort of the user is reduced.
For example, with tabular data (DataFrame) it is more semantically helpful to think of the index (the rows) and the columns rather than axis 0 and axis 1.

##### Mutability
All Pandas data structures are value mutable (can be changed) and except Series all are size mutable. Series is size immutable.
Note − DataFrame is widely used and one of the most important data structures. Panel is used much less.
Series
Series is a one-dimensional array like structure with homogeneous data. For example, the following series is a collection of integers 10, 23, 56, …
10
23
56
17
52
61
73
90
26
72

#### Key Points
Homogeneous data
Size Immutable
Values of Data Mutable

##### DataFrame
DataFrame is a two-dimensional array with heterogeneous data. For example,
Name
Age
Gender
Rating
Steve
32
Male
3.45
Lia
28
Female
4.6
Vin
45
Male
3.9
Katie
38
Female
2.78
The table represents the data of a sales team of an organization with their overall performance rating. The data is represented in rows and columns. Each column represents an attribute and each row represents a person.
Data Type of Columns
The data types of the four columns are as follows −
Column
Type
Name 
String 
Age 
Integer 
Gender 
String 
Rating 
Float 
Key Points
Heterogeneous data
Size Mutable
Data Mutable

## Panel
Panel is a three-dimensional data structure with heterogeneous data. It is hard to represent the panel in graphical representation. But a panel can be illustrated as a container of DataFrame.

#### Key Points
* Heterogeneous data
* Size Mutable
* Data Mutable
