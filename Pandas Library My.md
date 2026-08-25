
**df.head(<no of rows[default = 5]>)** -> shows top 5 rows of dataset{works on series as well as data frame}.


**df.tail(<no of rows[default = 5]>)** -> shows bottom 5 rows of dataset{works on series as well as data frame}.


**df.shape[<optional value of either 0 or 1 to represent row or column>]** -> gives the number of rows and columns in a tuple datatype.


**df.info()** -> shows all info about the columns present in dataset and helps in identifying missing values from dataset by showing number of non null values in each column.


**df.describe()** -> shows stats of only numerical columns in the dataset like count, mean, std[standard deviation], min, 25,50 and 75 percentile and the max values.


**df[‘<column_name>’]** -> shows only that column.{a series datatype}


**df[[‘col1’, ‘col2’, ‘col3’, …]]** -> shows these columns.{a data frame datatype}


**df.iloc[<index of row>]** -> gives the row of that index in a series datatype.


**df[[‘row1’, ‘row2’, ‘row3’, …]]** -> gives these rows in a data frame.


**df.iloc[min_row_index : max_row_index+1 : optional step_size]** -> gives the rows in a data frame datatype.


**df.iloc[min_row_index : max_row_index+1 : optional step_size, min_col_index : max_col_index+1 : optional step_size]** -> gives data frame datatype with desired rows and columns.


**df[‘col_name’] == or > or < or >= or <= or != ‘<value>’**{like a condition} -> give a boolean series of True and False to show whether the condition is being satisfied or not. Storing it in a variable “**mask**”, then **df[mask]** gives a data frame with all rows where this condition is being satisfied. Multiple can be handled like **df[mask1 & mask2]**.{& - Boolean And}


**df[‘col_name’].value_counts()** -> works on series datatype and returns a series of all different types of values in that column along with the number of how many times they appear. Also all binary mathematical operations can be performed on two series obtained by this function if they have the same indexes. Can also be stored in a variable say **myseries**.


**myseries.index** -> gives the unique values in that column without the count.


**df[‘col_name’].value_counts().plot(kind=‘<kind of graph you want>’)** or **df[‘col_name’].plot(kind=‘<kind of graph you want>’)** -> will give the required graph{it is important to import matplotlib.pyplot to actually see the graph}.


**df.sort_values(‘col_name’, <optional parameter -> ascending=False>, <optional parameter -> inplace=True>)** -> sorts the data frame based on the column. If inplace = true then change is permanent.{also works on series}


**df.sort_values([‘col1’,’col2’], <optional parameter -> ascending=[False, True]>, <optional parameter -> inplace=True>)** -> to sort based on multiple columns and decide ascending or descending for each.