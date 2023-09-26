## CodeWars Kata - Counting Vowels

[Link to the Kata](https://www.codewars.com/kata/54ff3102c1bad923760001f3/train/cpp)

### Problem Statement
Return the number (count) of vowels in the given string. We will consider a, e, i, o, u as vowels for this Kata (but not y). The input string will only consist of lower case letters and/or spaces.

### Solution

```cpp
#include <string>
#include <unordered_set>

using namespace std;

int getCount(const string& inputStr){
  unordered_set<char> vowels = {'a', 'e', 'i', 'o', 'u'};
  
  return count_if(inputStr.begin(), inputStr.end(), [vowels](char c){
    return vowels.find(c) != vowels.end();
  });
}
```

**Explanation**:

- The solution leverages `std::unordered_set` to hold the vowels. This container provides constant-time lookups on average.
- We then use `std::count_if` to iterate through each character of the input string.
- The lambda function `&vowels](char c) { return vowels.find(c) != end(vowels); }` checks if a character is in our `vowels` set. The `&vowels` in the lambda capture list means we are capturing the `vowels` set by reference, allowing us to use it inside the lambda. It is passed as the predicate to `std::count_if` to determine if a character is a vowel or not.

### Key Concepts

- `std::unordered_set`: An STL container that holds a unique set of objects. It provides constant-time lookups for unique keys.
- `std::count_if`: An STL algorithm that counts elements in a range that satisfy a certain predicate.
- **Lambda Functions**: In C++, lambda functions provide a concise way to represent anonymous functions. They can capture external variables, be passed as arguments, and can also be returned as results. They are a core part of modern C++ programming, offering both functionality and efficiency.

### Tags

- `#std/unordered_set`
- `#std/algorithm`
- `#lambda`
- `#cpp`

---

## Alternate

```c++
#include <string>

using namespace std;

bool is_vowel(char c) {
  return (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u');
}

int getCount(const string& inputStr) {
  return count_if(inputStr.begin(), inputStr.end(), is_vowel);
}
```

