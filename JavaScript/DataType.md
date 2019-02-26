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
##
##
##
##
##
##
