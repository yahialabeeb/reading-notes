## Unit tests:
#### They are pieces of code to exercise the input, the output and the behaviour of your code. You can write them anytime you want.

## Test-Driven Development:
#### Is a strategy to think (and write!) tests first.

## important 
* Arrange: organize the data needed to execute that piece of code (input);
* Act:  execute the code being tested (exercise the behaviour);
* Assert: after executing the code, you will check if the result (output) is the same as you were expecting.

The cycle is made by three steps:
* 🆘 Write a unit test and make it fail
* ✅ Write the feature and make the test pass! 
* 🔵 Refactor the code — the first version doesn’t need to be the beautiful one 

## Notes
* The greatest advantage about TDD is to craft the software design first
* Your code will be more reliable: after a change you can run your tests and be in peace
* Beginning may be hard — and that’s fine. You just need to practice!



# What does the if __name__ == “__main__”: do?

## special __name__ variable will be one of two things
1.If the python interpreter is running that module as the main program,the __name__ variable to have a value “__main__”.
2.If this file is being imported from another module, __name__ will be set to the module’s name.

## Advantages : 

* Every Python module has it’s __name__ defined and if this is ‘__main__’, it implies that the module is being run standalone by the user and we can do corresponding appropriate actions.
* If you import this script as a module in another script, the __name__ is set to the name of the script/module.
* Python files can act as either reusable modules, or as standalone programs.
* if __name__ == “main”: is used to execute some code only if the file was run directly, and not imported