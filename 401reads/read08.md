# List Comprehensions

## Syntax
> my_new_list = [ expression for item in list ]
1. the expression we’d like to carry out.
2. the object that the expression will work on.
3. we need an iterable list of objects to build our new list from.

## Create a List Using Loops and List Comprehension in Python
* list comprehensions reduce the code necessary to complete rather complicated task when working with a list.

```python 
# create a list using a for loop
squares = []

for x in range(10):
    # raise x to the power of 2
    squares.append(x**2)

print(squares)
```

## Multiplying Parts of a List
```python
# create a list with list comprehensions
multiples_of_three = [ x*3 for x in range(10) ]

print(multiples_of_three)
```
By taking advantage of list comprehensions, it’s possible to work on only part of a list. For instance, if you only wanted the even numbers in a given range, you could find them using a filter. Also you can multiply every number in a list by a certain  

## Show the first letter of each word using Python

* List comprehensions can make solving issues involving strings much easier using simplified expressions. These methods can save time and precious lines of code.

```python
authors = ["Ernest Hemingway","Langston Hughes","Frank Herbert","Toni Morrison",
    "Emily Dickson","Stephen King"]
letters = [ name[0] for name in authors ]
print(letters)
```

## Lower/Upper case converter using Python
* Making use of Python’s lower() and upper() methods, we’ll use list comprehension to achieve this common task. 

```python
lower_case = [ letter.lower() for letter in ['A','B','C'] ]
upper_case = [ letter.upper() for letter in ['a','b','c'] ]
```

## Print numbers only from a given string
* Extract numbers from a string.

```python
user_data = "Elvis Presley 987-654-3210"
phone_number = [ x for x in user_data if x.isdigit()]
```

## Parsing a file using list comprehension

* It’s also possible to read files in Python using list comprehension.

```python
file = open("dreams.txt", 'r')
poem = [ line for line in file ]
```
## Using functions in list comprehensions

* Filtering elements from the list can be done using additional arguments. 
```python
# add a filter so we only double even numbers
even_nums = [double(x) for x in range(1,10) if x%2 == 0]
print(even_nums)
```
* Additional arguments can be added to create more complex logic
```python 
nums = [x+y for x in [1,2,3] for y in [10,20,30]]
print(nums)
```