## Errors & Exceptions
There are two kinds of errors in Python:
* **Syntax errors** occur when Python can’t interpret our code, since we didn’t follow the correct syntax for Python. These are errors you’re likely to get when you make a typo, or you’re first starting to learn Python.
* **Exceptions** occur when unexpected things happen during execution of a program, even if the code is syntactically correct. There are different types of built-in exceptions in Python, and you can see which exception is thrown in the error message.
  * **ValueError**: An object of the correct type but inappropriate value is passed as input to a built-in operation or function.
  * **AssertionError**: An assert statement fails.
  * **IndexError**: A sequence subscript is out of range.
  * **KeyError**: A key can't be found in a dictionary.
  * **TypeError**: An object of an unsupported type is passed as input to an operation or function.
  
|EXAMPLE EXCEPTION|HOW WOULD YOU TRY TO HANDLE THE EXCEPTION?|
|:---|:---|
|NameError: name 'abc_dict' is not defined|Identifier is not found in the local or global namespace. Make sure the reference to the identifier is correctory added to the code.|
|UnboundLocalError|You are trying to access a local variable before it is defined. Make sure local scope of variable in function is defined or value assigned to it.|
|ValueError: too many values to unpack (expected 2)|Assignation error. Inconsistency in how many values being unpacked and how many variables the values should be assigned to.|
|TypeError: unsupported operand type(s) for +: 'int' and 'str'|An operation or function is applied to an object of inappropriate type - e.g., trying to concatenate a string and integer. Change the datatype for one of the values (e.g chang int to str)|

## Handling Errors
### Try Statement
We can use `try` statements to handle _exceptions_. There are four clauses you can use:

* `try`: This is the only *mandatory* clause in a `try` statement. The code in this block is the first thing that Python runs in a `try` statement.
* `except`: If Python runs into an _exception_ while running the `try` block, it will jump to the `except` block that handles that _exception_.
* `else`: If Python runs into no exceptions while running the `try` block, it will run the code in this block after running the `try` block.
* `finally`: Before Python leaves this `try` statement, it will run the code in this `finally` block under any conditions, even if it's ending the program. E.g., if Python ran into an error while running code in the `except` or `else` block, this `finally` block will still be executed before stopping the program.

### Specifying Exceptions
We can actually specify which error we want to handle in an `except` block like this:
```
try:
    # some code
except ValueError:
    # some code
```
Now, it catches the _ValueError_ exception, but not other exceptions. If we want this handler to address more than one type of exception, we can include a parenthesized tuple after the `except` with the exceptions.
```
try:
    # some code
except (ValueError, KeyboardInterrupt):
    # some code
```
Or, if we want to execute different blocks of code depending on the exception, you can have multiple `except` blocks.
```
try:
    # some code
except ValueError:
    # some code
except KeyboardInterrupt:
    # some code
```

## Accessing Error Messages
`Exception` is just the base class for all built-in exceptions. You can learn more about Python's exceptions [here](https://docs.python.org/3/library/exceptions.html#bltin-exceptions). When you handle an exception, you can still access its error message like this:
```
try:
    # some code
except ZeroDivisionError as e:
   # some code
   print("ZeroDivisionError occurred: {}".format(e))
```
This would print something like this:
```
ZeroDivisionError occurred: integer division or modulo by zero
```
So you can still access error messages, even if you handle them to keep your program from crashing!

If you don't have a specific error you're handling, you can still access the message like this:
```
try:
    # some code
except Exception as e:
   # some code
   print("Exception occurred: {}".format(e))
```





