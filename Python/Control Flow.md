## Truth Value & False Value
If we use a _non-boolean_ object as a condition in an `if` statement in place of the boolean expression, Python will check for its _truth value_ and use that to decide whether or not to run the indented code. By default, the _truth value_ of an object in Python is considered `True` unless specified as `False` in the documentation.

Here are most of the built-in objects that are considered `False` in Python:
* constants defined to be false: `None` and `False`
* zero of any numeric type: `0`, `0.0`, `0j`, `Decimal(0)`, `Fraction(0, 1)`
* empty sequences and collections: `'""`, `()`, `[]`, `{}`, `set()`, `range(0)`

```
errors = 3
if errors:
    print("You have {} errors to fix!".format(errors))
else:
    print("No errors to fix!")
```
In this code, `errors` has the truth value True because it's a non-zero number, so the error message is printed. This is a nice, succinct way of writing an `if` statement.