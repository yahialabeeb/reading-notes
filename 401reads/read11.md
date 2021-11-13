
## JupyterLab 
* a next-generation web-based user interface for Project Jupyter.

## Uses of JupyterLab
* You can arrange multiple documents and activities side by side in the work area using tabs and splitters.
* Documents and activities integrate with each other, enabling new workflows for interactive computing.

### Documents and Activities integrate example:
* Code Consoles provide transient scratchpads for running code interactively, with full support for rich output. A code console can be linked to a notebook kernel as a computation log from the notebook, for example.

* Kernel-backed documents enable code in any text file (Markdown, Python, R, LaTeX, etc.) to be run interactively in any Jupyter kernel.

* Notebook cell outputs can be mirrored into their own tab, side by side with the notebook, enabling simple dashboards with interactive controls backed by a kernel.

* Multiple views of documents with different editors or viewers enable live editing of documents reflected in other viewers..

* Also it offers a unified model for viewing and handling data formats
* JupyterLab offers customizable keyboard shortcuts and the ability to use key maps from vim, emacs, and Sublime Text in the text editor.






## NumPy
* It is a commonly used Python data analysis package. it speed up your workflow, and interface with other packages in the Python ecosystem
* NumPy is a package for working with multidimensional arrays.

### Numpy 2-Dimensional Arrays
* we work with multidimensional arrays.

### Creating A NumPy Array
* We can create a NumPy array using the numpy.array function. If we pass in a list of lists, it will automatically create a NumPy array with the same number of rows and columns. 

### Alternative NumPy Array Creation Methods
* you can create an array where every element is zero.
* You can also create an array where each element is a random number using numpy.random.rand.
### Using NumPy To Read In Files
* It’s possible to use NumPy to directly read csv or other files into arrays

### Indexing NumPy Arrays
*  We can use array indexing to select individual elements, groups of elements, or entire rows and columns. 
### Slicing NumPy Arrays
*  Select all the elements from the starting index up to but not including the ending index. 

### Assigning Values To NumPy Arrays
* We can also use indexing to assign values to certain elements in arrays.
* We can do the same for slices. To overwrite an entire column.

### 1-Dimensional NumPy Arrays
*  A 1-dimensional array only needs a single index to retrieve an element.
### N-Dimensional NumPy Arrays

* One way to think of this is as a list of lists of lists.

### NumPy Data Types
* Numpy Data Types are distinct from Python types like float and str. This is because the core of NumPy is written in a programming language called C, which stores data differently than the Python data types. 
* You can find the data type of a NumPy array by accessing the dtype property.

### Converting Data Types

* You can use the numpy.ndarray.astype method to convert an array to a different type. The method will actually copy the array, and return a new array with the specified data type. 
### NumPy Array Operations
* Single Array Math  (/, *, -, +, ^)
* Multiple Array Math
* Broadcasting (To match up elements)

### NumPy Array Methods
* NumPy also has several methods that you can use for more complex calculations on arrays.
* An example of this 
1. numpy.ndarray.sum method.
2. numpy.ndarray.mean — finds the mean of an array.
3. numpy.ndarray.std — finds the standard deviation of an array.
4. numpy.ndarray.min — finds the minimum value in an array.
5. numpy.ndarray.max — finds the maximum value in an array.

### NumPy Array Comparisons
* Subsetting => One of the powerful things we can do with a Boolean array and a NumPy array is select only certain rows or columns in the NumPy array.

### Reshaping NumPy Arrays

* We can change the shape of arrays while still preserving all of their elements. This often can make it easier to access array elements. The simplest reshaping is to flip the axes, so rows become columns, and vice versa. 
* We can accomplish this with the numpy.transpose function.
* We can use the numpy.ravel function to turn an array into a one-dimensional representation.

### Combining NumPy Arrays
* With NumPy, it’s very common to combine multiple arrays into a single unified array. We can use numpy.vstack to vertically stack multiple arrays. 

[Free NumPy cheat sheet](https://s3.amazonaws.com/dq-blog-files/numpy-cheat-sheet.pdf)