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
A _switch_ statement allows a program to evaluate an expression by attempting to match the expression's value to a _case label_. If a match is found, the program jumps to the statement(s) associated with the matched label and continues executing at that point. Note that execution will continue sequentially through all the statements starting at the jump point unless there is a call to `break;`, which exits the switch statement. A switch statement looks like this:
```
switch (expression) {
    case label1:
        statement1;
        break;
    case label2:
        statement2;
        break;
    case label3:
        statement3;
        statement4;
        break;
    default:
        statement;
}
```
The program first looks for a `case` clause with a label matching the value of **expression**, then transfers control to the matching clause and executes the associated statements. If no matching label is found, the program looks for the optional _default_ clause and, if found, transfers control to that clause and executes the statements associated with it. If no `default` clause is found, the program continues executing after the end of the switch statement.
### The `default` Clause
By convention, the `default` clause is always listed last. This is because the statements are checked sequentially, so you run into the following issues if you use the `default` label in an earlier clause:

* If the `default` case is listed _before_ (above) a case that matches **expression**, it will match the `default` case instead. This means the statements associated with the programmed match case won't be executed.
* If the `default` case doesn't have a break statement, any statements in the case label immediately following it will be executed.

### The `break;` Statement
The `break` statement is optional, but you'll typically see one at the end of each `case` clause to ensure that the program breaks out of the switch statement once the statements associated with a matched case are executed. Once the flow of execution hits `break;`, it exits the switch statement and continues executing at the next line following the end of the switch statement; if the `break` statement is omitted, the program continues executing the next statement in the switch statement — even if its case label doesn't match **expression**.

### Multi-Criteria Case
```
switch (expression) {
    case label1:
    case label2:
    case label3:
        statement1;
        break;
    case label4:
    case label5:
        statement2;
        break;
    case label6:
    case label7:
    case label8:
        statement3;
        statement4;
        break;
    default:
        statement;
}
```







