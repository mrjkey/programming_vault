
# CodeWars Kata - Counting Set Bits

[Link to kata placeholder](https://www.codewars.com/kata/526571aae218b8ee490006f4/train/cpp)

## Problem Statement
Write a function that takes an integer as input, and returns the number of bits that are equal to one in the binary representation of that number. You can guarantee that the input is non-negative.

Example: The binary representation of 1234 is 10011010010, so the function should return 5 in this case.

## Solution

```cpp
#include <bitset>

unsigned int countBits(unsigned long long n) {
    return std::bitset<64>(n).count();  // using 64 bits because the input type is unsigned long long
}
```

**Explanation**:
- We use `std::bitset<64>` to convert the number `n` to its binary representation.
- The `count()` function of `std::bitset` returns the number of bits set to 1 in its representation. Thus, eliminating any need for manual counting.

## Key Concepts
- **std::bitset**: Represents a fixed-size sequence of binary digits. Bitsets can be manipulated by standard logic operators, converted to and from strings, and integers.
- **std::bitset::count()**: Returns the number of bits set to 1 in the bitset's representation.

## Tags
#std/bitset #bit-manipulation #algorithms

--- 

You can directly copy-paste this content into Obsidian without any additional modifications, and it should render with the intended formatting.