## CodeWars Kata - Sum Strings as Numbers

[Placeholder Link to the Kata](https://www.codewars.com/kata/5324945e2ece5e1f32000370/train/cpp)

### Problem Statement

Given the string representations of two integers, return the string representation of the sum of those integers.

Example:
```
sumStrings('1','2') // => '3'
```
A string representation of an integer will contain no characters besides the ten numerals "0" to "9".

### Solution

#### Code:

```cpp
#include <string>
#include <algorithm>

std::string sum_strings(const std::string& a, const std::string& b) {
    std::string result;
    auto it_a = a.rbegin(), it_b = b.rbegin();
    int carry = 0;

    while (it_a != a.rend() || it_b != b.rend() || carry) {
        int num_a = (it_a != a.rend()) ? *it_a - '0' : 0; // Convert char to int and handle end of string
        int num_b = (it_b != b.rend()) ? *it_b - '0' : 0;

        int sum = num_a + num_b + carry;
        result.push_back((sum % 10) + '0');  // Convert int to char
        carry = sum / 10;

        if (it_a != a.rend()) ++it_a;
        if (it_b != b.rend()) ++it_b;
    }

    std::reverse(result.begin(), result.end());  // As we appended from least significant digit, we reverse to get the correct order
    return result;
}
```

#### Explanation:

This solution simulates the process of addition that we're familiar with from school. Starting from the least significant digit (rightmost), we traverse each string using reverse iterators. For each corresponding pair of digits, we perform the addition, consider any carried over value from the previous addition, and append the result to our output string. The `- '0'` trick is used to convert char digits to integers for arithmetic operations. At the end, since we appended from the least significant to most, we reverse the result string to get it in the correct order.

### Key Concepts

- **Reverse Iterators**: `.rbegin()` and `.rend()` methods provide reverse iterators for strings, enabling traversal from the end.
  
- **Character to Integer Conversion**: By subtracting the ASCII value of '0' from a char digit, we get its integer value. This is achieved with `*it_a - '0'`.

- **std::reverse()**: Used to reverse the order of characters in a string or elements in a container.

### Tags

`#cpp` `#strings` `#algorithm` `#iteration` `#std/reverse`

---


## Alternate

```c++
#include <string>

using namespace std;

string sum_strings(const string &a, const string &b)
{
  string result;
  int carry = 0, n = max(a.size(),b.size());
  for (int i = 0 ; i < n ; i++)
  {
    if (i < a.size()) carry += a[a.size()-1-i]-'0';
    if (i < b.size()) carry += b[b.size()-1-i]-'0';
    result.push_back('0'+carry%10);
    carry /= 10;
  }
  result.push_back(carry+'0');
  while (result.size() > 1 && result.back() == '0')
    result.pop_back();
  reverse(result.begin(), result.end());
  return result;
}
```
