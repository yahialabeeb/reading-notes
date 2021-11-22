# shutil — High-level File Operations

## Copying Files
* copyfile() copies the contents of the source to the destination and raises IOError if it does not have permission to write to the destination file.

```python 
shutil.copyfile('shutil_copyfile.py', 'shutil_copyfile.py.copy')
```
* The implementation of copyfile() uses the lower-level function copyfileobj(). While the arguments to copyfile() are filenames, the arguments to copyfileobj() are open file handles. The optional third argument is a buffer length to use for reading in blocks.
```python 
shutil.copyfileobj(input, output)
```

* The copy() function interprets the output name like the Unix command line tool cp
* copy2() works like copy(), but includes the access and modification times in the metadata copied to the new file.
```python 
shutil.copy('shutil_copy.py', 'example')
shutil.copy2('shutil_copy2.py', 'example')
```
## Copying File Metadata
* To copy the permissions from one file to another, use copymode()
```
shutil.copymode('shutil_copymode.py', 'file_to_change.txt')
```
* To copy other metadata about the file use copystat()
```
shutil.copystat('shutil_copymode.py', 'file_to_change.txt')
```
## Working With Directory Trees
* To copy a directory from one place to another, use copytree().
 * copytree() accepts two callable arguments to control its behavior

```
shutil.copytree('../shutil', '/tmp/example')
```
* To remove a directory and its contents, use rmtree().
```
shutil.rmtree('/tmp/example')
```
* To move a file or directory from one place to another, use move().
```
shutil.move('example.txt', 'example.out')
```
## Finding Files
* The which() function scans a search path looking for a named file.
```
print(shutil.which('no-such-program'))
```
* If no file matching the search parameters can be found, which() returns None.
## Archives
* get_archive_formats() returns a sequence of names and descriptions for formats supported on the current system.

* Use make_archive() to create a new archive file
* Extract the archive with unpack_archive()
## File System Space
* disk_usage() returns a tuple with the total space, the amount currently being used, and the amount remaining free.


