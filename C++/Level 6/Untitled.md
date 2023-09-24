https://www.codewars.com/kata/514b92a657cdc65150000006/train/cpp

```
---
Title: 'CodeWars Kata - Multiples of 3 and 5'
---

## Link
[Placeholder Link](#)

## Problem Statement
If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6, and 9. The sum of these multiples is 23. Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in. Additionally, if the number is negative, return 0. Note: If the number is a multiple of both 3 and 5, only count it once.

## Solution

### Code
```cpp
int solution(int number) {
    if (number < 0) {
        return 0;
    }

    int sum = 0;
    for (int i = 0; i < number; ++i) {
        if (i % 3 == 0 || i % 5 == 0) {
            sum += i;
        }
    }
    return sum;
}
```

### Explanation
The function starts by checking if the input number is negative. If so, it immediately returns `0`. We then initialize a `sum` variable to `0`, which will keep track of the accumulated sum of the desired multiples. 

A `for` loop is used to iterate over every number from `0` to `number - 1`. Inside the loop, a conditional checks if the current number (`i`) is a multiple of either `3` or `5`. If the condition is true, the current number is added to the sum. 

Finally, the sum is returned as the output of the function.

## Key Concepts

- **Conditional Statements**: Used to check if a number is negative or if a number is a multiple of 3 or 5.
- **Loops**: Specifically, the `for` loop is used to iterate over each number from 0 to one less than the input number.
- **Modulus Operator (%)**: Used to determine if a number is a multiple of another number. If `a % b` is `0`, then `a` is a multiple of `b`.

## Tags
#loops #conditionals #modulus-operator #basics #integers
```