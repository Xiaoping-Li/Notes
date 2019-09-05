In short, variables _label_ and _store_ data in memory. There are only a few things you can do with variables:
* Create a variable with a descriptive name.
* Store or update information stored in a variable.
* Reference or “get” information stored in a variable.

It is important to distinguish that _variables_ are not _values_; they contain values and represent them with a name.

## var, let, const
`var`, short for _variable_, is a JavaScript `keyword` that creates, or _declares_, a new variable. There are a few general rules for naming variables:
* Variable names cannot start with numbers.
* Variable names are case sensitive.
* Variable names cannot be the same as _keywords_.

### let, var
* The `let` (or `var`) keyword signals that the variable can be reassigned a different value.
* The `let` (and even `var`) can declare a variable without assigning the variable a value. In such a case, the variable will be automatically initialized with a value of `undefined`.

### const
* Constant variables must be assigned a value when _declared_. If you try to declare a `const` variable without a value, you’ll get a `SyntaxError`.
* A `const` variable cannot be _reassigned_ because it is **constant**. If you try to reassign a `const` variable, you’ll get a `TypeError`.

## Truthy and Falsy Assignment
The list of `falsy values` includes:
* 0
* Empty strings like "" or ''
* `null` which represent when there is no value at all
* `undefined` which represent when a declared variable lacks a value
* `NaN`, or Not a Number
