# Conditions
## if-else Statements
Use the `if` statement to execute a statement if a logical condition (i.e., some statement that evaluates to true or false) is _true_. Use the optional `else` clause to execute a statement only in the event that the if condition evaluates to _false_. Additionally, you can compound the statements using the `else-if` clause to test multiple conditions in sequence.  
Chaining related logic conditions using else-if in this way has a few benefits:
* When there are multiple conditions being checked within a chained sequence of statements, only the first logical condition to evaluate to true will be executed. This also means that after one of the logical conditions evaluates to true, any subsequent logical statements in the block will be skipped over. 
* If a later condition check is reached, you know that all the preceding condition checks within that chain all evaluated to false. This means you don't have to re-check certain conditions.  
### Falsy Values  
The following six values are known as _Falsy_ values, meaning they evaluate to _false_:
* false
* undefined
* null
* 0
* NaN
* "" (i.e., the empty string)
All other values, including all objects, evaluate to _true_ when used as the condition in a conditional statement. 

### Conditional (Ternary) Operator
The conditional (ternary) operator is the only JavaScript operator that takes three operands, and it's used as a shortcut for the _if_ statement. The basic syntax is:
```
condition ? trueStatement : falseStatement
```
You can essentially read the `?` as the word "then" and the `:` as the word "else". If _condition_ evaluates to true, then _trueStatement_ is executed; else, _falseStatement_ is executed. 

## switch Statements
