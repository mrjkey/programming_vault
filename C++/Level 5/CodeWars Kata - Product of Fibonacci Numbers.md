# CodeWars Kata - Product of Fibonacci Numbers

[Placeholder Link to the Kata](https://www.codewars.com/kata/5541f58a944b85ce6d00006a/train/cpp)

## Problem Statement

The Fibonacci numbers are the numbers in the following integer sequence (Fn):

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, ...

Given a number, say `prod` (for product), we search two Fibonacci numbers \( F(n) \) and \( F(n+1) \) verifying:

\[ F(n) \times F(n+1) = prod \]

The function `productFib` takes an integer (`prod`) and returns an array:

- If \( F(n) \times F(n+1) = prod \), return \[ F(n), F(n+1), true \].
- Otherwise, return \[ F(n), F(n+1), false \] with \( F(n) \times F(n+1) > prod \) and \( F(n) \) being the smallest value to satisfy this condition.

## Solution

### Code

```cpp
#include <vector>
#include <tuple>

typedef unsigned long long ull;
class ProdFib
{
public:
    static std::vector<ull> productFib(ull prod)
    {
        ull a = 0, b = 1;

        while (a * b < prod)
        {
            std::tie(a, b) = std::make_tuple(b, a + b);
        }

        return {a, b, a * b == prod ? 1ULL : 0ULL};
    }
};
```

### Explanation

1. We initiate with the first two Fibonacci numbers: `a=0` and `b=1`.
2. A loop runs until the product of the two numbers (`a*b`) is less than the given product (`prod`).
3. Within the loop, the next Fibonacci numbers are obtained. The idiomatic approach in C++ using `std::tie` and `std::make_tuple` enables the simultaneous update of `a` and `b`.
4. After the loop, we ascertain if `a*b` equals `prod`. If true, `{a, b, 1}` is returned, else `{a, b, 0}` is returned.

## Key Concepts

- **std::tie**: A function in the C++ STL that allows unpacking of tuple elements into variables.
- **std::make_tuple**: A utility function to create a tuple.
- **Fibonacci Sequence**: A series of numbers where each number (Fibonacci number) is the sum of the two preceding ones.

## Tags

#fibonacci #std/tie #std/make_tuple #std/vector

---


## Alternate Solution

```c++
#include <vector>
typedef unsigned long long ull;
class ProdFib
{
public:
  static std::vector<ull> productFib(ull prod)
  {
  		ull a = 0, b = 1;
      while (a * b < prod) {
      		std::swap(a, b);
          b += a;
      }
      return {a, b, ((a*b == prod) ? true : false)};
  }
};
```


