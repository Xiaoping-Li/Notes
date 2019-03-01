# Arithmetic Operators
## Operator Types
* **Unary**: A _unary_ operator requires a single operand, either before or after the operator, following this format:
```
operand operator
operator operand
```
For example, in the expression `a++`, `++` is a unary operator.
* **Binary**: A _binary_ operator requires two operands, one before the operator and one after the operator, following this format:
```
operand1 operator operand2
```
For example, in the expression `a + b = c`, `+` is a binary operator.
* **Ternary**: There is one _ternary_ operator, the `conditional operator`. For example, in the expression `a ? b : c`, the use of `?` and `:` in this manner constitutes the ternary operator. 

## Arithmetic Operators
An _arithmetic operator_ takes numeric values (either literals or variables) as its operands and returns a `single numeric value`. The standard arithmetic operators are `addition (+), subtraction (-), multiplication (*), and division (/). Other arithmetic operators are remainder (%), unary negation (-), unary plus (+), increment (++), decrement (--), and exponentiation (**)`.
* Exponentiation (\*\*): We use this operator in the form `operand1 ** operand2`. This operator is a part of ECMAScript2016 feature set. For example:
```
2 ** 3 // evaluates to 8
3 ** 2 // evaluates to 9
5 ** 4 // evaluates to 625 
```
* Unary Negation (-): We use this operator in the form -operand. For example:
```
-4 // evaluates to -4
-(-5) // evaluates to 5 (not --5)
```
* Unary Plus (+): We use this operator in the form +operand. For example:
```
+4 // evaluates to 4
+(-4) // evaluates to -4
```
* Increment (++): We use this operator in the _prefix_ and _postfix_ forms, forms `++operand` and `operand++`. The _prefix_ form, `++operand`, **increments the operand by 1 and then returns the value of the operand**. The _postfix_ form, `operand++`, **returns the value of the operand and then increments the operand's value by 1.**
* Decrement (--): We use this operator in the _prefix_ and _postfix_ forms, forms `--operand` and `operand--`. The _prefix_ form, `--operand`, **decrements the operand by 1 and then returns the value of the operand**. The _postfix_ form, `operand--`, **returns the value of the operand and then decrements the operand's value by 1.**  


**Note:** 
* _prefix_ form update state now
* _postfix_ form update in the second sequence not now

