# Python Scope
## scope 
* the area of a program in which you can unambiguously access that name
## scope Types

Global scope: The names that you define in this scope are available to all your code.

Local scope: The names that you define in this scope are only available or visible to the code within the scope.

## Namespace
These are the concrete mechanisms that Python uses to store names. They’re stored in a special attribute called .__dict__.

## Using the LEGB Rule for Python Scope
### The letters in LEGB stand for Local, Enclosing, Global, and Built-in.
1. Local scope : This Python scope contains the names that you define inside the function. These names will only be visible from the code of the function. It’s created at function call, not at function definition 

2. Enclosing (or nonlocal) scope is a special scope that only exists for nested functions. If the local scope is an inner or nested function, then the enclosing scope is the scope of the outer or enclosing function. This scope contains the names that you define in the enclosing function. The names in the enclosing scope are visible from the code of the inner and enclosing functions.

3. Global scope is the top-most scope in a Python program, script, or module. This Python scope contains all of the names that you define at the top level of a program or a module. Names in this Python scope are visible from everywhere in your code.

4. Built-in scope is a special Python scope that’s created or loaded whenever you run a script or open an interactive session. This scope contains names such as keywords, functions, exceptions, and other attributes that are built into Python. Names in this Python scope are also available from everywhere in your code.

> when you use nested functions, names are resolved by first checking the local scope. Then, Python looks at all enclosing scopes of outer functions from the innermost scope to the outermost scope. If no match is found, then Python looks at the global and built-in scopes. If it can’t find the name, then you’ll get an error.

* When the function returns, the local scope is destroyed and the names are forgotten.

### Modifying global names is generally considered bad programming practice because it can lead to code that is:

1. Difficult to debug: Almost any statement in the program can change the value of a global name.
2. Hard to understand: You need to be aware of all the statements that access and modify global names.
3. Impossible to reuse: The code is dependent on global names that are specific to a concrete program.

### builtins
* Standard library module in Python 3.x that All of Python’s built-in objects live in it.

## Modifying the Behavior of a Python Scope
### Python provides two keywords that allow you to modify the content of global and nonlocal names. 
* These two keywords are:
1. global
* you can use a global statement. With this statement, you can define a list of names that are going to be treated as global names.
2. nonlocal
* With a nonlocal statement, you can define a list of names that are going to be treated as nonlocal.

## Using Enclosing Scopes as Closures
### closure  
* an inner or nested function that carries information about its enclosing scope, even though this scope has completed its execution.
* Closures provide a way to retain state information between function calls. This can be useful when you want to write code based on the concept of lazy or delayed evaluation.

## Bringing Names to Scope With import
* import can bring the names in those separate modules to your __main__ module. 
*from <module> import <name>. This way, you can use the imported name directly in your code

## Using Scope Related Built-In Functions

* built-in functions that can help you out to get information about a Python scope or namespace
1. globals() : built-in function that returns a reference to the current global scope or namespace dictionary.
2. locals() :  This function updates and returns a dictionary that holds a copy of the current state of the local Python scope or namespace.
3. dir() : gettint a list containing the names that live in the global scope. You can also use dir() to inspect the list of names or attributes of different objects.
4. vars() : a Python built-in function that returns the .__dict__ attribute of a module, class, instance, or any other object which has a dictionary attribute.

## Conclusion
* The scope of a variable or name defines its visibility throughout your code.
* In Python, scope is implemented as either a Local, Enclosing, Global, or Built-in scope. 
* When you use a variable or name, Python searches these scopes sequentially to resolve it. If the name isn’t found, then you’ll get an error. 
