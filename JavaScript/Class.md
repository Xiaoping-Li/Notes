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
    
### The Constructor Method
* The _constructor method_ is a special method we use to create and initialize objects of a class.
* A class can only have _one_ special method with the name `constructor`, and attempting to write a class containing more than one constructor method will throw a _SyntaxError_.
* To implement _inheritance_, we can use the `super` keyword in a constructor to call a parent class constructor.

### Prototype Methods
```
class Polygon {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
    getArea() {
        return this.height * this.width;
    }
}

const square = new Polygon(10, 10);
console.log(square.getArea());
```

### Static Methods
_Static methods_ are methods relevant to all instances of a class — not just any one instance. These methods receive information from their arguments and not a class instance, which allows us to invoke a class' static methods without creating an instance of the class. In fact, we actually _can't_ call a static method on an instantiated class object (attempting to do so throws a _TypeError_).

We define a class' static methods using the `static` keyword. We typically use these methods to create _utility_ functions for applications, as they can't be called on class objects.
```
class Point {
    constructor(x, y) {
        this.x = x;
        this.y = y;
    }
    static distance(a, b) {
        const dx = a.x - b.x;
        const dy = a.y - b.y;
        return Math.sqrt(dx * dx + dy * dy);
    }
}

const p1 = new Point(5, 5);
const p2 = new Point(10, 10);

// The correct way to call a static method
console.log(Point.distance(p1, p2));

// Attempt to call a static method on an instance of the class
try {
    console.log(p1.distance(p1, p2));
}
catch (exception) {
    console.log(exception.name + ': ' + exception.message);
}
```
Output:
```
7.0710678118654755
TypeError: p1.distance is not a function
```

### Inheritance
In essence, this construct allows us to create an object prototype or class that's an _extension_ of another object prototype or class. A class inheriting from some other class (referred to as a superclass or parent class) is called a subclass (or child class). The subclass inherits the superclass' methods and behaviors, but it can also declare new ones or even override existing ones.

### Subclassing with the extends Keyword
We use the `extends` keyword in class declarations or class expressions to create a child class (i.e., subclass).
```
class Animal {
    constructor(name) {
        this.name = name;
    }
    speak() {
        console.log(this.name, 'speaks.');
    }
}

class Dog extends Animal {
    speak() {
        console.log(this.name, 'barks.');
    }
}

```

We can also extend functional classes:
```
// functional class
function Animal(name) {
    this.name = name;
}

Animal.prototype.speak = function() {
    console.log(this.name, 'speaks.');
}

// class declarations
class Dog extends Animal {
    speak() {
        console.log(this.name, 'barks.');
    }
}
```

### Superclass Calls Using the `super` Keyword
We use the _super_ keyword to call functions on an object's parent.
```
class Animal {
    constructor(name) {
        this.name = name;
    }
    speak() {
        console.log(this.name, 'speaks.');
    }
}

class Dog extends Animal {
    speak() {
        super.speak();
        console.log(this.name, 'barks.');
    }
}
```

### Extending an Object
The ability to extend multiple classes from the same superclass (or model multiple object types after the same prototype) is powerful because it provides us with certain implied guarantees about the basic functionality of the subclasses; as extensions of the parent class, subclasses are guaranteed to (at minimum) have the superclass' fields, methods, and functions.

In this example, we call the superclass constructor using `super()`, override a superclass function (`speak()`), add an additional property (`collarColor`), and add a new subclass method (`collar()`).
```
class Animal {
    constructor(name) {
        this.animalType = 'Animal'
        this.name = name;
    }
    type() {
        console.log(this.name, 'is type', this.animalType);
    }
    speak() {
        console.log(this.name, 'speaks.');
    }
}

class Dog extends Animal {
    constructor(name, collarColor) {
        super(name);
        this.animalType = 'Dog';
        this.collarColor = collarColor;
    }
    speak() {
        console.log(this.name, 'barks.');
    }
    collar() {
        console.log(this.name, 'has a', this.collarColor, 'collar.');
    }
}

let spot = new Dog('Spot', 'red');
spot.type();
spot.speak();
spot.collar();

// Because the Animal constructor only expects one argument,
// only the first value passed to it is used
spot = new Animal('Spot', 'white');
spot.type();
spot.speak();
try {
    spot.collar();
}
catch (exception) {
    console.log(exception.name + ': ' + exception.message
    + ' (collar is a method of Dog, not Animal).');
}
```
