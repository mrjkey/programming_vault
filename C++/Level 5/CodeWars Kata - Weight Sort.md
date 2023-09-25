# CodeWars Kata - Weight Sort

[Link to Kata - Placeholder](https://www.codewars.com/kata/55c6126177c9441a570000cc/train/cpp)

## Problem Statement

My friend John and I are members of the "Fat to Fit Club (FFC)". John is worried because each month a list with the weights of members is published and each month he is the last on the list which means he is the heaviest.

The challenge is to modify the order of this list. It was decided to attribute a "weight" to numbers. The weight of a number will be from now on the sum of its digits.

Given a string with the weights of FFC members in normal order, the task is to provide this string ordered by "weights" of these numbers.

Notes:
- It may happen that the input string has leading, trailing whitespaces and more than a unique whitespace between two consecutive numbers.
- When two numbers have the same "weight", class them as if they were strings (alphabetical ordering) and not numbers.

## Solution

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <sstream>
#include <numeric>

class WeightSort
{
public:
    static std::string orderWeight(const std::string &strng)
    {
        std::vector<std::string> numbers;
        std::istringstream ss(strng);
        std::string token;
        while (ss >> token)
            numbers.push_back(token);

        std::sort(numbers.begin(), numbers.end(), 
        [](const std::string &a, const std::string &b) 
        {
            auto getWeight = [](const std::string &num) 
            {
                return std::accumulate(num.begin(), num.end(), 0, 
                [](int sum, char ch) 
                {
                    return sum + ch - '0';  
                });
            };

            int weightA = getWeight(a);
            int weightB = getWeight(b);

            return weightA == weightB ? a < b : weightA < weightB;
        });

        std::string result;
        for (const auto &num : numbers)
            result += num + " ";

        if (!result.empty())
            result.pop_back();

        return result;
    }
};
```

### Explanation

1. Parse the input string and store all the numbers in a vector.
2. Sort the numbers in the vector based on their weights.
3. The weight of a number is calculated as the sum of its digits.
4. If two numbers have the same weight, they are compared as strings.
5. Finally, convert the sorted numbers back to a string.

## Key Concepts

- `std::istringstream`: Provides a way to treat strings as input streams, which can be useful for parsing space-separated tokens or numbers from a string.
- `std::accumulate`: Computes the sum (or other accumulative operations) of elements in a range.
- Lambda Functions: Provides a concise way to declare functions without needing a name or full function definition.

## Tags

- #std/vector
- #std/istringstream
- #std/algorithm
- #std/numeric
- #lambda-functions
- #string-parsing

---