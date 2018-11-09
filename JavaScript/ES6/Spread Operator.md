**Spread syntax** allows an iterable such as an array expression or string to be expanded in places where zero or more arguments 
(for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more 
key-value pairs (for object literals) are expected.

_from freecodecamp_
ES6 introduces the spread operator, which allows us to expand arrays and other expressions in places where multiple parameters or elements are expected.

The ES5 code below uses `apply()` to compute the maximum value in an array:
```
var arr = [6, 89, 3, 45];
var maximus = Math.max.apply(null, arr); // returns 89
```

