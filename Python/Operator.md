## Arithmatic Operator
## Comparison Operator
## Logical Operator
**and**: Returns the first false value; if not found returns last.

**or**: Returns the first true value; if not found returns last.

**not**: flips the Boolean value of the operand

**and, or** return one of the operands; **not** returns only `True` or `False`.

## Membership Operator
**in**: evaluates if object on left side is _included in_ object on right side

**not in**: evaluates if object on left side is _not included in_ object on right side
```
name = ['me', 'you', 'she', 'he']
print('her' in name)

output: False
```

## Identity Operators
**is**: evaluates if both sides have the same identity

**is not**: evaluates if both sides have different identities

### Checking for Equality vs. Identity: == vs. is
```
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(a == b)   --->>> True
print(a is b)   --->>> True
print(a == c)   --->>> True
print(a is c)   --->>> Fasle
```
List **a** and list **b** are _equal_ and _identical_. List **c** is _equal_ to **a** (and **b** for that matter) since they have the same contents. But **a** and **c** (and **b** for that matter, again) point to two different objects, i.e., they aren't _identical_ objects. That is the difference between checking for _equality vs. identity_.

