## CodeWars Kata - Disemvowel Trolls

[Link to Kata](https://www.codewars.com/kata/52fba66badcd10859f00097e/train/cpp)

### Problem Statement

Trolls are attacking your comment section! A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat. Your task is to write a function that takes a string and return a new string with all vowels removed. For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!". Note: for this kata y isn't considered a vowel.

### Solution

**Code:**
```cpp
#include <string>
#include <algorithm>

std::string disemvowel(const std::string& str) {
    std::string result = str;  // Make a copy of the input string
    
    // Use remove_if with a lambda to remove all the vowels
    auto end = std::remove_if(result.begin(), result.end(), [](char c) {
        c = std::tolower(c);
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    });
    
    // Erase the vowels from the end of the string
    result.erase(end, result.end());
    
    return result;
}
```

**Explanation:**
In this solution, we first make a copy of the input string, ensuring we don't modify the original string passed by const reference. Next, we use the `std::remove_if` function, combined with a lambda function, to check each character and determine if it's a vowel. The lambda function converts the character to lowercase to handle both uppercase and lowercase vowels. The `std::remove_if` function moves all the vowels to the end of the string and returns an iterator pointing to the first vowel. Using the `erase` member function of the string, we remove all the characters from that iterator to the end of the string, effectively removing all the vowels. 

### Key Concepts

- `std::remove_if`: Reorders the elements in a container such that the elements for which the predicate returns `true` are placed at the end. It returns an iterator pointing to the first of these elements.
- **Lambda Functions**: An anonymous function or a function without a name. Introduced in C++11, it allows defining a function on-the-fly.
- `std::tolower`: Converts a given character to lowercase.
- `std::string::erase`: Removes a portion of the string, effectively reducing its length.

**Tags:** #std/algorithm #std/string #lambda #string-manipulation

---