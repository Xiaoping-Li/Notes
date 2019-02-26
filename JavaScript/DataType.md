# JavaScript's Data Types
The latest ECMAScript standard defines seven data types:

* A _primitive value_ or data type is data that is `not an object` and `has no methods`. All primitives are **immutable**, meaning they cannot be changed. There are six primitive types:
    * Number
    * String
    * Boolean
    * Symbol
    * Null
    * Undefined
* The seventh data type is Object
## Number Data Type
According to the ECMAScript standard, all numbers are `double-precision 64-bit binary format IEEE 754-2008`, meaning there is _no specific type_ for integers.
* Maximum Value for a Number
The `MAX_VALUE` property has a value of approximately 1.79E+308, or 2^1024 . Values larger than `Number.MAX_VALUE` are represented as `Infinity`.
* Minimum Value for a Number
The `MIN_VALUE` property is the smallest positive value of the Number type closest to 0, not the most negative number, that JavaScript can represent. `MIN_VALUE` has a value of approximately 5 * 10 ^ (-324) . Values smaller than `Number.MIN_VALUE` ("underflow values") are converted to 0.
* Symbolic Numbers: There are three symbolic number values:
   * `Infinity`: This is any number divided by 0, or an attempt to multiply Number.MAX_VALUE by an integer > 1.
   * `-Infinity`: This is any number divided by -0, or an attempt to multiply Number.MAX_VALUE by an integer < -1.
   * `NaN`: This stands for "Not-a-Number" and denotes an unrepresentable value (i.e.,(-1)^(1/2) ).
* The `isSafeInteger` Method: The `Number.isSafeInteger()` method determines whether the provided value is a number that is a safe integer.
   * `Maximum Safe Integer`: The `Number.MAX_SAFE_INTEGER` constant has a value of 9007199254740991, or 2^53 - 1.
   * `Minimum Safe Integer`: The `Number.MIN_SAFE_INTEGER` constant has a value of -9007199254740991, or -2^53 + 1.
## String Data Type
* A string value is a chain of zero or more Unicode characters (i.e., letters, digits, and punctuation marks) that we use to represent text. We include string literals in our scripts by enclosing them in single (') or double (") quotation marks. Double quotation marks can be contained in strings surrounded by single quotation marks (e.g., '"' evaluates to "), and single quotation marks can be contained in strings surrounded by double quotation marks (e.g., "'" evaluates to ').
* Notice that JavaScript does not have a type to represent a single character. To represent a single character in JavaScript, you create a string that consists of only one character. A string that contains zero characters ("") is an empty (zero-length) string.
* Unlike in languages like C, JavaScript strings are immutable. This means that once a string is created, it is not possible to modify it. However, it is still possible to create another string based on an operation on the original string. For example:
   * A substring of the original by picking individual letters or using String.substr().
   * A concatenation of two strings using the concatenation operator (+) or String.concat().

##
##
##
##
##
