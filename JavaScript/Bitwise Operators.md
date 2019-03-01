# Bitwise Operators
## Binary Number Basics
* The binary, or base-2, numeral system is a way for us to express numbers. It's called binary because it only uses _two symbols_, 0 and 1, to express these numbers. Examples of binary numbers are 1011, 100011, and 111.
* The number of symbols in a number system is called its _base_ or _radix_. This is why we often see binary numbers referred to as base-2 (because each digit is in {0, 1}), and decimal numbers referred to as base-10 (because each digit is in {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}).
* We use the notation `(?)b` to discuss numbers with different radixes, where `?` is the number and `b` is the base. For example, (1101)2 is the binary equivalent of the decimal number (13)10.
* Each digit in a binary number is called a **bit**.

## Base-10 (Decimal) to Base-2 (Binary) Conversions
We use the following algorithm to convert a decimal integer to a binary number:

1. Take the decimal integer, divide it by 2, and record the quotient (the number of times 2 divided the integer) and the remainder (the number of units left over from the division, which will always be 0 or 1).
2. Repeat step 1 on the quotient until the quotient becomes 0.
3. Look at the sequence of remainders. The remainder from the first division operation corresponds to the binary number's _least significant bit_ (LSB) and the remainder from the last division operation corresponds to the number's _most significant bit_ (MSB). To get our binary number, we simply need to concatenate these remainder bits from most to least significant.

## Base-2 (Binary) to Base-10 (Decimal) Conversions
Let's say we have a binary number with _d_ bits. We use the following summation to calculate its base- integer value:
```
let sum = 0;
for (let i = 0; i < d; i++) {
  let bit = bits[i];
  sum += bit * Math.pow(2, i); 
}
```

## Representing Negative Base-10 Numbers in Base-2
In this explanation, we're representing our integers as 32-bit signed binary numbers. To represent an integer, _-n_, in binary, we perform the following steps:

1. Find the 32-bit binary representation of n.
2. Take the **1**'s complement. We do this by inverting all the binary number's bits (i.e., every 0 becomes a 1, and every 1 becomes a 0).
3. Take the **2**'s complement by adding 1 to the **1**'s complement.
The **2**'s complement is the binary representation of _-n_.

## Bitwise Operation Conventions
Conceptually, the bitwise logical operators work as follows:

* The operands are converted to 32-bit integers, meaning they're expressed as sequences of 32 zeroes and ones. Any number larger than 32 bits is reduced to 32 bits by cutting off and discarding its excess _most significant bits_. The example below shows a binary integer before and after it's converted to a 32-bit integer:
  ```
  Before: 11100110111110100000000000000110000000000001
  After:              10100000000000000110000000000001
  ```
* Each bit in the first operand is paired with the corresponding bit in the second operand from least to most significant. In other words, the first LSB matches the first LSB, the second LSB matches the second LSB, and so on.
* The operator is applied to each pair of bits so that the resulting number is constructed bitwise (i.e., bit-by-bit).

### Bitwise AND (`&`)
This operator performs the _AND_ operation on each pair of bits. Given two binary numbers, a and b, the result of an **AND** operation on the corresponding bits at each position i (i.e., ai & bi) is 1 if and only if both ai and bi are 1. The truth table for the bitwise **AND** operation is:

ai | bi | ai & bi
--- | --- | :---:
0 | 0 | 0
0 | 1 | 0
1 | 0 | 0
1 | 1 | 1

For example, 101 & 110 = 100.

### Bitwise OR (`|`)
This operator performs the _OR_ operation on each pair of bits. Given two binary numbers, a and b, the result of an **OR** operation on the corresponding bits at each position i (i.e., ai | bi) is 1 if ai and/or bi are 1. The truth table for the bitwise **OR** operation is:

ai | bi | ai \| bi
--- | --- | :---:
0 | 0 | 0
0 | 1 | 1
1 | 0 | 1
1 | 1 | 1

For example, 0101 | 0110 = 0111.

### Bitwise XOR (`^`)
This operator performs the _XOR_ operation on each pair of bits. Given two binary numbers, a and b, the result of an **XOR** operation on the corresponding bits at each position i (i.e., ai ^ bi) is 1 if either ai or bi is 1 (i.e., the values of the two operands are different). The truth table for the bitwise **XOR** operation is:

ai | bi | ai ^ bi
--- | --- | :---:
0 | 0 | 0
0 | 1 | 1
1 | 0 | 1
1 | 1 | 0

For example, 0101 ^ 0110 = 0011.

### Bitwise NOT (`~`)
This operator performs the _NOT_ operation on each pair of bits in a number. Given a binary number, a, the **NOT** operation (i.e., ~a) inverts each bit in the number. The truth table for the bitwise **NOT** operation is:

a | ~a 
--- | --- 
0 | 1 
1 | 0 

For example, ~101 = 010.

### Example
```
// Bitwise AND
     9 (base 10) = 00000000000000000000000000001001 (base 2)
    14 (base 10) = 00000000000000000000000000001110 (base 2)
                   --------------------------------
14 & 9 (base 10) = 00000000000000000000000000001000 (base 2) = 8 (base 10)

// Bitwise OR
     9 (base 10) = 00000000000000000000000000001001 (base 2)
    14 (base 10) = 00000000000000000000000000001110 (base 2)
                   --------------------------------
14 | 9 (base 10) = 00000000000000000000000000001111 (base 2) = 15 (base 10)

// Bitwise XOR
     9 (base 10) = 00000000000000000000000000001001 (base 2)
    14 (base 10) = 00000000000000000000000000001110 (base 2)
                   --------------------------------
14 ^ 9 (base 10) = 00000000000000000000000000000111 (base 2) = 7 (base 10)

// Bitwise NOT
 9 (base 10) = 00000000000000000000000000001001 (base 2)
               --------------------------------
~9 (base 10) = 11111111111111111111111111110110 (base 2) = -10 (base 10)
```



