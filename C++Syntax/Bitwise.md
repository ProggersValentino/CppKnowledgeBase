
Bitwise operations are operations that directly change the binary of bits for a value. there are many key operators that are used to perform bitwise

```cpp
std::bitset<8> bitsA = 0100 0110;
std::bitset<8> bitsB = 0001 0011;

//AND operator
std::bitset<8> bit& = bitsA & bitsB; // 0000 0010

//OR operator
std::bitset<8> bit| = bitsA | bitsB; // 0101 0111

//XOR operator
std::bitset<8> bit^ = bitsA ^ bitsB; // 0101 0101

//NOT operator
std::bitset<8> bit^ = ~(bitsA); // 1010 1001

//Left shift operator
std::bitset<8> bit<< = bitsA << 3; // 0100 0110 = 0011 0000

//right shift operator
std::bitset<8> bit>> = bitsA >> 3; // 0100 0110 = 0000 1000

```

## Truth Table for comparison operations

The truth table below establishes how each bit comparison operator works

| X   | Y   | X&Y | X\|Y | X^Y | ~(X) |
| --- | --- | --- | ---- | --- | ---- |
| 0   | 1   | 0   | 1    | 1   | 1    |
| 1   | 0   | 0   | 1    | 1   | 0    |
| 1   | 1   | 1   | 1    | 0   | 0    |
| 0   | 0   | 0   | 0    | 0   | 1    |

### Left and right shift

Say we want to shift a set of bits left or right:

```cpp
std::bitset<8> bitsA = 0110 0111;
```

then we can use the `<<` or `>>` to achieve out shift, generally the format is the value you want to bit shift, left or right shift operator then how much you want to shift it by:
```cpp
bitsA << 3 //0011 1000
//we want to left shift the bits of `bitsA` by 3 
```

which as you can see shifts the bits in the dedicated direction, the final result is **VERY** dependent on the amount of bits for each variable, as for instance, because `bitsA` only has the capacity of `8-bits` when shifting to left or right, if they go out of the variable's bit bound then they are lost forever as show above.

But if `bitsA` had the bit capacity of `16-bits` then all the bits would be maintained:

```cpp
std::bitset<16> bitsA = 0000 0000 0110 0111;

bitsA <<= 3; //0000 0011 0011 1000
```

