
Title: **CodeWars Kata - Multiplication Placeholder**

Link to the kata: `[Placeholder Link to Kata]`
[Kata URL](https://www.codewars.com/kata/50654ddff44f800200000004/train/cpp)
## Problem Statement
The given code does not execute properly. Your task is to figure out why and then correct it. The code provided is:

```cpp
int multiply(int a, int b)
{
    a * b;
}
```

## Solution

### Code:
```cpp
int multiply(int a, int b)
{
    return a * b;
}
```

### Explanation:
The initial code performed the multiplication of `a` and `b` but did not return any value, making the function ineffective. In the solution, we simply added the `return` statement to ensure the multiplied result is returned to the caller.

## Key Concepts

- **Return Statement in C++**: In a non-void function in C++, it's essential to use the `return` statement to provide a value back to the caller. If a function declares a return type, it must return a value of that type.

Tags: #cpp #return-statement 

---