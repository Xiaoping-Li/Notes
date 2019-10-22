## Errors & Exceptions
There are two kinds of errors in Python:
* **Syntax errors** occur when Python can’t interpret our code, since we didn’t follow the correct syntax for Python. These are errors you’re likely to get when you make a typo, or you’re first starting to learn Python.
* **Exceptions** occur when unexpected things happen during execution of a program, even if the code is syntactically correct. There are different types of built-in exceptions in Python, and you can see which exception is thrown in the error message.
  * **ValueError**: An object of the correct type but inappropriate value is passed as input to a built-in operation or function.
  * **AssertionError**: An assert statement fails.
  * **IndexError**: A sequence subscript is out of range.
  * **KeyError**: A key can't be found in a dictionary.
  * **TypeError**: An object of an unsupported type is passed as input to an operation or function.

## Handling Erros: Try Statement
We can use `try` statements to handle _exceptions_. There are four clauses you can use:

* `try`: This is the only *mandatory* clause in a `try` statement. The code in this block is the first thing that Python runs in a `try` statement.
* `except`: If Python runs into an _exception_ while running the `try` block, it will jump to the `except` block that handles that _exception_.
* `else`: If Python runs into no exceptions while running the `try` block, it will run the code in this block after running the `try` block.
* `finally`: Before Python leaves this `try` statement, it will run the code in this `finally` block under any conditions, even if it's ending the program. E.g., if Python ran into an error while running code in the `except` or `else` block, this `finally` block will still be executed before stopping the program.




