https://www.hackerrank.com/challenges/js10-class/topics/javascript-classes
# Classes in JavaScript

## Functional Classes
In this section, we'll discuss some of the ways we can use functions to simulate the behavior of classes.
### Using Functions
1. Define a normal JavaScript function.
2. Create an object by using the `new` keyword.
3. Define properties and methods for a created object using the `this` keyword.
```
function Fruit (type) {
    this.type = type;
    this.color = 'unknown';
    this.getInfo = getFruitInformation;
}

function getFruitInformation() {
    return 'This ' + this.type + ' is ' + this.color + '.';
}
```
We can also define the _getInfo_ function _internally_:
```
function Fruit (type) {
    this.type = type;
    this.color = 'unknown';
    this.getInfo = function() {
        return 'This ' + this.type + ' is ' + this.color + '.';
    }
}
```
Create instance by using `new` keyword:
```
let lime = new Fruit('Mexican lime');
console.log(lime.getInfo());

lime.color = 'green';
console.log(lime.getInfo());
```
Output:
```
This Mexican lime is unknown.
This Mexican lime is green.
```
### The Prototype Property
The drawback of _internally_ defining the _getInfo_ function is that it recreates that function every time we create a new Fruit object. Fortunately, every function in JavaScript has something called a _prototype property_, which is empty by default. We can think of a function's prototype as an object blueprint or paradigm; when we add methods and properties to the prototype, they are accessible to _all_ instances of that function. This is especially useful for _inheritance_ (discussed below).

We can add a function to our constructor function's prototype like so:
```
function Fruit (type) {
    this.type = type;
    this.color = 'unknown';
}

Fruit.prototype.getInfo = function() {
    return 'This ' + this.type + ' is ' + this.color + '.';
}
```

### Using Object Literals
We can use object literals to define an object's properties and functions by initializing a variable with a comma-separated list of property-value pairs enclosed in curly braces.
```
let lime = {
    type: 'Mexican lime',
    color: 'green',
    getInformation: function() {
        return 'This ' + this.type + ' is ' + this.color + '.';
    }
}

console.log(lime.getInformation());

lime.color = 'yellow';
console.log(lime.getInformation());
```
Output:
```
This Mexican lime is green.
This Mexican lime is yellow.
```

### Singleton Class Using a Function
A _singleton_ class is a design pattern that restricts a class to a **single instance**. When we assign the value of `new function(){...}` to a variable, the following happens:

1. We define an anonymous constructor function.
2. We invoke the anonymous constructor function with the `new` keyword.
```
let lime = new function() {
    this.type = 'Mexican lime';
    this.color = 'green';
    this.getInformation = function() {
        return 'This ' + this.type + ' is ' + this.color + '.';
    };
}

console.log(lime.getInformation());

lime.color = 'yellow';
console.log(lime.getInformation());
```
Output:
```
This Mexican lime is green.
This Mexican lime is yellow.
```

## Classes
JavaScript classes, introduced in _ECMAScript 6_, are essentially syntactic sugar over JavaScript's existing prototype-based inheritance that don't actually introduce a new object-oriented inheritance model. `This syntax is a means of more simply and clearly creating objects and deal with inheritance.`

We define classes in two ways:

### Class Declarations
One way to define a class is using a class declaration. To declare a class, we use the **class** keyword and follow it with the class' name. Ideally, we always write class names in _TitleCase_.
```
class Polygon {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
}

let p = new Polygon(1, 2);
```
**Note**: An important difference between function declarations and class declarations is that function declarations are hoisted (i.e., can be referenced before they're declared) but class declarations are not. This means we must first declare our class before attempting to access (or reference) it; if we fail to do so, our code throws a _ReferenceError_.

### Class Expressions
_Class expressions_ are another way to define a class, and they can be either _named_ or _unnamed_. The name given to a named class expression is _local_ to the class' body.
* Unnamed Class Expression
    ```
    let Polygon = class {
        constructor(height, width) {
            this.height = height;
            this.width = width;
        }
    };
    ```
* Named Class Expression
    ```
    let Polygon = class Polygon {
        constructor(height, width) {
            this.height = height;
            this.width = width;
        }
    };
    ```






