## Comparison Operators

### Equality Operators (==) / Inequality (!=)
* Equality (==)  
The equality operator is a binary operator that compares two operands, returning _true_ if they are deemed to be equal. It works by converting the operands if they are not of the same type, then applying strict comparison. If both operands are primitive types, it will compare their values (i.e., 1 == 1 evaluates to true). If both operands are objects, then JavaScript compares their internal references; this means it checks to see if both operands point to the same object (i.e., location) in memory.
```
console.log(0 == false);           // true
console.log(0 == null);            // false      
console.log(0 == undefined);       // false
console.log(null == undefined);    // true
```
* Inequality (!=)  
The inequality operator is a binary operator that returns _true_ if the operands are not equal. If the two operands are of different types, JavaScript attempts to convert the operands to an appropriate type to compare them. If both operands are objects, then JavaScript compares the internal references to see if they are not equal (i.e., refer to different objects in memory).

### Identity or Strict Equality (===) / Non-Identity or Strict Inequality (!==)
* Identity or Strict Equality (===): The identity operator returns true if both of the following conditions are satisfied:
  * The operands are strictly equal.
  * The operands are of the same type.
* Non-Identity or Strict Inequality (!==): The non-identity operator returns true if the operands satisfy any of the following conditions:
  * The operands are not equal.
  * The operands are not of the same type.

## Relational Operators
### Greater Than Operator (>)
### Greater Than or Equal Operator (>=)
### Less Than Operator (<)
### Less Than or Equal Operator (<=)


## Logical Operators
### Logical AND (&&)
### Logical OR (||)
### Logical NOT (!)
### Short-Circuit Evaluation
