## CodeWars Kata - Middle Character

[Link to the kata](https://www.codewars.com/kata/56747fd5cb988479af000028/train/cpp)

### Problem Statement

You are given a word. Your job is to return the middle character of the word. If the word's length is odd, return the middle character. If the word's length is even, return the middle 2 characters.

**Examples**:
- `getMiddle("test")` should return "es"
- `getMiddle("testing")` should return "t"
- `getMiddle("middle")` should return "dd"
- `getMiddle("A")` should return "A"

### Solution

**Code**:

```cpp
#include <string>

std::string get_middle(const std::string& input) 
{
    size_t length = input.size();
    if (length % 2 == 1) 
    {
        return std::string(1, input[length / 2]);
    } 
    else 
    {
        return input.substr((length / 2) - 1, 2);
    }
}
```

**Explanation**:
- The `size()` function is used to determine the length of the string.
- For odd-length strings, the middle character is returned using the `std::string` constructor.
- For even-length strings, the `substr` method is used to extract the two middle characters.

### Key Concepts

- `std::string::size()`: Returns the number of characters in the string.
- `std::string::substr()`: Returns a newly constructed string object with its value initialized to a copy of a substring of the original string.

### Tags

- `#string`
- `#std/string`
- `#std/substr`
- `#algorithm`

---

## My bad attempt

```c++
std::string get_middle(std::string input) 
{
  int length = input.length();
  
  std::string result;
  
  bool is_even = length % 2 == 0 ? true : false;
  
  // 4/2 = 2, 1 and 2
  // 7/2 = 3.5 = 3
  
  for(int i =0; i< length; i++){
    if(is_even){
      if(i == (length/2) or i == (length/2)-1){
        result += input[i];
      }
    }else{
      if(i == (length/2)){
        result += input[i];
      }
    }
  }

  return result;
}
```