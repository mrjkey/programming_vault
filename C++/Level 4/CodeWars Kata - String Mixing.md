# CodeWars Kata - String Mixing

- Link: [Placeholder Link to Kata](https://www.codewars.com/kata/5629db57620258aa9d000014/train/cpp)

## Problem Statement

Given two strings s1 and s2, visualize how different the two strings are, taking into account only lowercase letters (a to z). Count the frequency of each lowercase letter in both strings. The task is to produce a string in which each lowercase letter of s1 or s2 appears as many times as its maximum if this maximum is strictly greater than 1. These letters will be prefixed by the number of the string where they appear with their maximum value and `:`. If the maximum is in both s1 and s2, the prefix is `=:`. 

## Solution

### Code

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <map>
#include <numeric>

class Mix
{
public:
    static std::string mix(const std::string &s1, const std::string &s2);
};

std::string Mix::mix(const std::string &s1, const std::string &s2)
{
    std::map<char, int> freq1, freq2;

    for (char c : s1)
        if (c >= 'a' && c <= 'z')
            freq1[c]++;
    for (char c : s2)
        if (c >= 'a' && c <= 'z')
            freq2[c]++;

    std::vector<std::string> results;

    for (char c = 'a'; c <= 'z'; c++)
    {
        if (freq1[c] > 1 || freq2[c] > 1)
        {
            if (freq1[c] > freq2[c])
                results.push_back("1:" + std::string(freq1[c], c));
            else if (freq1[c] < freq2[c])
                results.push_back("2:" + std::string(freq2[c], c));
            else
                results.push_back("=:" + std::string(freq1[c], c));
        }
    }

    std::sort(results.begin(), results.end(), [](const std::string &a, const std::string &b) {
        return a.size() > b.size() || (a.size() == b.size() && a < b);
    });

    return std::accumulate(results.begin(), results.end(), std::string(), [](const std::string &a, const std::string &b) {
        return a + (a.empty() ? "" : "/") + b;
    });
}
```

### Explanation

1. Count the frequency of lowercase characters in both strings using maps (`freq1` and `freq2`).
2. Construct a result vector with the maximum frequency strings. If a character appears more times in `s1` than `s2`, it's prefixed with `1:`. If it appears more in `s2`, it's prefixed with `2:`. If the counts are equal, it's prefixed with `=:`.
3. Sort the results based on their length (longer strings first), and lexicographically for strings of equal length.
4. Use `std::accumulate` to construct the final result by joining the sorted strings with a `/` separator.

## Key Concepts

- **std::map**: An associative container that contains key-value pairs with unique keys. It allows for fast retrieval based on keys.
- **std::sort**: A sorting function to sort elements in a range.
- **std::accumulate**: A function to accumulate values in a range.
- **Lambdas**: Anonymous functions used for short operations like custom sorting or accumulating.

## Tags

- #std/map
- #std/vector
- #std/sort
- #std/accumulate
- #lambdas

---