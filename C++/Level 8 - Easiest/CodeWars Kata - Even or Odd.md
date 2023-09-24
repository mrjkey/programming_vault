
# CodeWars Kata - Even or Odd

[Link to Kata](https://www.codewars.com/kata/53da3dbb4a5168369a0000fe/train/cpp)

## Problem Statement
Create a function that takes an integer as an argument and returns "Even" for even numbers or "Odd" for odd numbers.

## Solution

```cpp
#include <string>

std::string even_or_odd(int number) 
{
    return number % 2 == 0 ? "Even" : "Odd";
}
```

### Explanation
The function leverages the modulo operator (`%`) to determine whether the input number is even or odd. If the number is divisible by 2 with no remainder (i.e., `number % 2 == 0`), the function returns "Even". Otherwise, it returns "Odd".

## Key Concepts

- **Modulo Operator `%`**: It returns the remainder of the division of one number by another. In the context of checking for even or odd, if a number modulo 2 results in 0, the number is even. Otherwise, it's odd.

## Tags
#int #modulo #conditional-operator #std/string
```

You can copy-paste the above content directly into an Obsidian note, and it will be formatted correctly with headers, code blocks, and relevant tags. Adjust the placeholder URL to point to the actual kata link when you have it.