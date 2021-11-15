# pandas

* Pandas help numpy turn arrays into dataframes
* Pandas are all about data table representatio

## Object creation

* Creating a Series by passing a list of values,
* Creating a DataFrame by passing a NumPy array, with a datetime index and labeled columns or by passing a dict of objects that can be converted to series-like

## Viewing data
* NumPy arrays have one dtype for the entire array, while pandas DataFrames have one dtype per column
* pandas finds the NumPy dtype that can hold all of the dtypes in the DataFrame.

### ways of viewing data:

1. df.describe() - gives a quick statistic summary of your data
2. df.T - Transposes your data
3. df.sort_index(axis=1, ascending=False) - Sorts by axis
4. df.sort_values(by=A) - Sorts by value
5. df.head(), and dt.tail()

## Selection
### Getting 
* df["A"] => Selecting a single column
* Selecting via [], which slices the rows.
### Selection by label
* df.loc[name_of_data[0]] => getting a cross section using a label.
* df.loc[:, ["A", "B"]] => Selecting on a multi-axis by label.
* df.loc["starting point value":"ending point value", ["A", "B"]] => Showing label slicing, both endpoints are included
* df.loc["point value", ["A", "B"]] => Reduction in the dimensions of the returned object
* df.loc[dates[0], "A"] => getting a scalar value

## Setting
* Setting a new column automatically aligns the data by the indexes
### Ways 
* df.at[dates[0], "A"] = 0 => by label
* df.iat[0, 1] = 0 => by position.
* assigning with a NumPy array

## Missing data
* pandas primarily uses the value np.nan to represent missing data. It is by default not included in computations. See the Missing Data section.

## Operations
### Stats
Operations in general exclude missing data.
### Apply
Applying functions to the data.
### String Methods
* Series is equipped with a set of string processing methods in the str attribute that make it easy to operate on each element of the array, as in the code snippet below.

## Merge
### Concat
* Concatenating pandas objects together with concat().

### Join
* SQL style merges. 

## Grouping

1. Splitting the data into groups based on some criteria

2. Applying a function to each group independently

3. Combining the results into a data structure

## Reshaping
* The stack() method “compresses” a level in the DataFrame’s columns
* The unstack() method unstacks the last level

## Pivot Tables

> Example of producing a pivot table
>pd.pivot_table(df, values="D, index=["A","B"], columns=["C"])

## Time Series

* Pandas has functionality for "performing resampling operations during frequency conversion"

> e.g., converting secondly data into 5 minute data
>rng = pd.date_range("1/1/2012", periods=100, freq="S")

* The following example is used to convert to another time zone:

> ts_utc.tz_convert("US/Eastern")

## Categoricals
pandas can include categorical data in a DataFrame

## Plotting
* The standard convention for referencing the matplotlib API
* The close() method is used to close a figure window
* The plot() method is a convenience to plot all of the columns with labels

## Getting data in/out
### CSV

Writing to a csv file.
> df.to_csv("foo.csv")
Reading from a csv file.

> pd.read_csv("foo.csv")
### HDF5 
Writing to a HDF5 Store.

> df.to_hdf("foo.h5", "df")
Reading from a HDF5 Store.
>pd.read_hdf("foo.h5", "df")

### EXCEL

Writing to an excel file.

> df.to_excel("foo.xlsx", sheet_name="Sheet1")

Reading from an excel file.

> pd.read_excel("foo.xlsx", "Sheet1", index_col=None, na_values=["NA"])
