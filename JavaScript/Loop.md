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
