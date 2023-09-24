# CodeWars Kata - Reverse Words

[Link Placeholder to Kata](https://www.codewars.com/kata/5264d2b162488dc400000001/train/cpp)

## Problem Statement
Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed. Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.

## Solution

```cpp
#include <string>
#include <sstream>
#include <algorithm>

std::string spinWords(const std::string &str) {
    std::istringstream iss(str); // Used for tokenizing the string
    std::ostringstream oss; // Used to gather our final result
    std::string word;

    bool isFirstWord = true;

    while (iss >> word) {
        if (word.size() >= 5) {
            std::reverse(word.begin(), word.end()); // Reverse the word if it has 5 or more letters
        }

        // To ensure we don't add an unnecessary space at the beginning
        if (!isFirstWord) {
            oss << " ";
        }

        oss << word; // Add the word to the final result
        isFirstWord = false;
    }

    return oss.str();
}
```

**Explanation**: 
1. The `std::istringstream` is used to tokenize the input string.
2. For each word, check if its length is 5 or more.
3. If the word length satisfies the condition, reverse it using `std::reverse`.
4. The word (reversed or not) is then added to the `std::ostringstream`.
5. The final string is returned from the `std::ostringstream`.

## Key Concepts

- `std::istringstream`: It's an input stream that operates on strings. It can be used to tokenize a string using the stream extraction operator.
- `std::ostringstream`: It's an output stream that operates on strings. It helps in constructing or accumulating strings.
- `std::reverse`: A function that reverses elements in a given range.

## Tags
- `#std/istringstream`
- `#std/ostringstream`
- `#std/reverse`
- `#string`
- `#algorithm`

---