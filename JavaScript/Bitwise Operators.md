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
2. Take the 1's complement. We do this by inverting all the binary number's bits (i.e., every 0 becomes a 1, and every 1 becomes a 0).
3. Take the 2's complement by adding 1 to the 1's complement.
The 's complement is the binary representation of .


