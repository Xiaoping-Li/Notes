# Loops
_Loops_ are a quick and easy way to repeatedly perform a series of instructions, and they are typically run a finite number of times. JavaScript has the following types of loops:

* for
* while
* do-while
* for-in
* for-of

## _for_
The _for_ statement creates a loop that consists of three optional expressions, enclosed in parentheses and separated by semicolons, followed by one or more statements that will be executed in the loop.
### Basic Syntax
```
for (initialization; condition; finalExpression) {
    statement(s);
}
```
### Components
* _initialization_: An expression or variable declaration that is typically used to initialize a counter variable.
* _condition_: This is the _termination condition_, which is an expression that's evaluated before each pass through the loop. If this expression evaluates to _true_, then _statement_ is executed. If the expression evaluates to _false_, execution jumps to the first line of code after the end of the loop. If this statement is omitted, then _condition_ always evaluates to true.
* _finalExpression_: An expression to be evaluated at the end of each loop iteration. This occurs before the next evaluation of _condition_.
* _statement_: The statement (or statements) that is executed each time _condition_ evaluates to _true_.  

It's important to note that:

* The _initialization_, _condition_, and _finalExpression_ in the head of the _for_ loop are optional, but are generally always used.
* The head of a _for_ loop typically looks like `for (var i = 0; i < maxValue; i++)`, where _maxValue_ is the maximum value you wish to iterate until.

## _while_
The _while_ statement creates a loop that executes its internal statement(s) as long as the specified _condition_ evaluates to _true_. The condition is evaluated before executing the statement.

### Basic Syntax
```
while (condition) {
    statement(s);
}
```
* _condition_: This is the _termination condition_, which is an expression that's evaluated before each pass through the loop. If this expression evaluates to _true_, then _statement_ is executed; if it evaluates to _false_, execution jumps to the first line of code after the end of the loop.
* _statement_: The statement (or statements) that is executed each time _condition_ evaluates to _true_.

## _do-while_
The _do-while_ statement creates a loop that executes its internal statement(s) until the specified _condition_ evaluates to _false_. The condition is evaluated after executing the internal statement(s), so the contents of the loop always execute _at least_ once.

### Basic Syntax
```
do {
    statement(s);
} while (condition);
```
* _condition_: This is the _termination condition_, and it's evaluated _after_ each pass through the loop (meaning the loop will always run at least once). Once the statement(s) inside the loop is executed, _condition_ is evaluated. If this expression evaluates to _true_, then _statement_ is executed again; if it evaluates to _false_, execution jumps to the first line of code after the end of the loop.
* _statement_: The statement (or statements) that is executed each time _condition_ evaluates to _true_.

## _for-in_
This loop iterates (in an arbitrary order) over the _name_ of each enumerable property in an object, allowing statements to be executed for each distinct property.

### Basic Syntax
```
for (var variable in object) {
    // insert code that uses variable here
}
```
* _variable_: A variable that refers to a different _property name_ during each iteration of the loop. You can declare this with `var` or `let`.
* _object_: The object whose enumerable properties are being iterated through.

## _for-of_
This loop iterates over iterable objects such as an _Array, Map, Set, String, TypedArray, arguments object_, etc. It essentially iterates over the _value_ of each distinct property in the structure, such as each letter in a word or each element in an array.

### Basic Syntax
```
for (let variable of iterable) {
    statement(s);
}
```
* _variable_: A variable that refers to a different _property value_ during each iteration of the loop. You can declare this with `var` or `let`.
* _object_: The object whose enumerable properties are being iterated through.


