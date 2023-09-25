# CodeWars Kata - Summing Big Numbers

[Link to the kata](https://www.codewars.com/kata/525f4206b73515bffb000b21/train/cpp)

## Problem Statement
Given two large numbers as strings, write a function that returns their sum also as a string.

**Example**:
- add("123", "321") -> "444"
- add("11", "99") -> "110"

## Solution

```cpp
#include <string>
#include <algorithm>

std::string add(const std::string& a, const std::string& b) {
    std::string result;
    int carry = 0, i = a.length() - 1, j = b.length() - 1;

    while(i >= 0 || j >= 0 || carry) {
        int sum = carry;
        if(i >= 0) sum += a[i--] - '0';
        if(j >= 0) sum += b[j--] - '0';

        result += (sum % 10) + '0';
        carry = sum / 10;
    }
    std::reverse(result.begin(), result.end());
    return result;
}
```

**Explanation**:

- We utilize two pointers, `i` and `j`, to traverse the input strings `a` and `b` respectively from the end to the beginning.
- `carry` is maintained to handle cases where the sum of two digits is 10 or greater.
- At each step, the current sum of digits from both strings (if present) and the `carry` is computed.
- The result for the current position is `sum % 10` and is appended to the `result` string.
- The new `carry` value is computed as `sum / 10`.
- After traversing both strings, if there's any remaining `carry`, it's appended to the result.
- Since we built the result in reverse, we use `std::reverse` to obtain the correct answer.

## Key Concepts

- **String Indexing**: Strings in C++ can be accessed similar to arrays, allowing for easy traversal and manipulation.
- **Character-to-Integer Conversion**: Subtracting `'0'` from a numeric character converts it to its corresponding integer. Adding `'0'` to an integer in the range [0,9] does the reverse.
- **std::reverse**: A method from the `<algorithm>` header, used to reverse elements in a range (like a string or a vector).

## Tags
#string #algorithm #std/algorithm #math/arithmetic #c++



## Alternate

```c++
using namespace std;

string add(string a, string b)
{
    a = string(max(a.size(), b.size()) + 1 - a.size(), '0') + a;
    b = string(a.size() - b.size(), '0') + b;
    for (int i = a.size()-1, carry = 0; i >= 0; i--)
    {
        int sum = a[i] + b[i] - 96 + carry;
        carry   = sum / 10;
        a[i]    = sum % 10 + '0';
    }
    int i = a.find_first_not_of('0');
    return 0 <= i ? a.substr(i) : a.substr(0, 1);
}
```

