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
   * A substring of the original by picking individual letters or using `String.substr()`.
   * A concatenation of two strings using the `concatenation operator (+)` or `String.concat()`.

## Boolean Data Type
A boolean represents a logical entity and can have one of two literal values: `true`, and `false`.
## Symbol Data Type
Symbols are new to JavaScript in ECMAScript Edition 6. A Symbol is a unique and immutable primitive value and may be used as the key of an Object property.
## Null Data Type
The null data type is an internal type that has only one value: `null`. This is a primitive value that represents the absence of any object value. A variable that contains null contains no valid number, string, boolean, array, or object. You can erase the contents of a variable (without deleting the variable) by assigning it the null value.
############################################################################################################################################################################################################################################################
## Undefined Data Type
The undefined value is returned when you use an object property that does not exist, or a variable that has been declared, but has never had a value assigned to it.
## Dynamic Typing
JavaScript is a loosely typed or dynamic language, meaning you don't need to declare a variable's type ahead of time and the language autmatically determines a variable's type while the program is being processed. That also means that you can reassign a single variable to reference different types.
## Declaration and Initialization
The first time a variable appears in your script is considered its `declaration`. The first mention of the variable sets it up in memory, and the name allows you to refer back to it in your subsequent lines of code. You should declare variables using the `var` keyword before using them. If you do not `initialize` a variable that was declared using the `var` keyword, it automatically takes on the value `undefined`.
## Coercion
In JavaScript, you can perform operations on values of different types without raising an exception. The JavaScript interpreter implicitly converts, or `coerces`, one of the data types to that of the other, then performs the operation. The rules for coercion of string, number, or boolean values are as follows:
* If you add a number and a string, the number is coerced to a string.
* If you add a boolean and a string, the boolean is coerced to a string.
* If you add a number and a boolean, the boolean is coerced to a number.



