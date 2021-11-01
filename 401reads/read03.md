#  FileIO & Exceptions

## Reading and Writing Files in Python
### What file is ?
* a file is a contiguous set of bytes used to store data. This data is organized in a specific format

#### file main parts:

* Header: metadata about the contents of the file
* Data: contents of the file as written by the creator or editor
* End of file (EOF): special character that indicates the end of the file

#### Line Endings
##### (CR+LF or \r\n) to end line and start another

#### Encoding 
* a translation from byte data to human readable characters. 

## Opening and Closing a File in Python

* Opening a file is done by invoking the open() built-in function.

* closing a file have 2ways 
1. The first way to close a file is to use the try-finally block
1. The second way to close a file is to use the with statement

### The second positional argument in build in function open is mode

| Character	| Meaning |
|----|----|
|'r' |	Open for reading (default) |
|'w' | Open for writing, truncating (overwriting) the file first |
|'rb' or 'wb' |	Open in binary mode (read/write using byte data)|

### Categories of file objects
1. Text files
1. Buffered binary files
1. Raw binary files

## Reading and Writing Opened Files

### Reading 

| Method | What It Does |
|----|----|
|.read(size=-1)	| This reads from the file based on the number of size bytes. If no argument is passed or None or -1 is passed, then the entire file is read.|
| .readline(size=-1) |This reads at most size number of characters from the line. This continues to the end of the line and then wraps back around. If no argument is passed or None or -1 is passed, then the entire line (or rest of the line) is read.|
|.readlines() | This reads the remaining lines from the file object and returns them as a list. |

### Writing 

Method | What It Does |
|----|----|
|.write(string) | This writes the string to the file.|
|.writelines(seq) | This writes the sequence to the file. No line endings are appended to each sequence item. It’s up to |you to add the appropriate line ending(s).|


## Python Exceptions

* Syntax errors occur when the parser detects an incorrect statement. 

### Raising an Exception
* We can use raise to throw an exception if a condition occurs. The statement can be complemented with a custom exception.

### The try and except Block
* The try and except block in Python is used to catch and handle exceptions. 

1. A try clause is executed up until the point where the first exception is encountered.
2. Inside the except clause, or the exception handler, you determine how the program responds to the exception.
3. You can anticipate multiple exceptions and differentiate how the program should respond to them.
4. Avoid using bare except clauses.

#### else statement 
* using the else statement, you can instruct a program to execute a certain block of code only in the absence of exceptions.
#### finally
* Everything in the finally clause will be executed. It does not matter if you encounter an exception somewhere in the try or else clauses.
