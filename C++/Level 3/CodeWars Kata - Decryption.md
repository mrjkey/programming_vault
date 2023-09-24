[kata url](https://www.codewars.com/kata/52cf02cd825aef67070008fa/train/cpp)


---

## CodeWars Kata - [Kata Name]

[Link to the kata](#)

### Problem Statement

General Patron is faced with a problem: his intelligence has intercepted some secret messages from the enemy, but they are all encrypted. Those messages are crucial to getting the jump on the enemy and winning the war. However, even the smartest programmers weren't able to crack it. So the general is asking you, his most odd but brilliant programmer. You are expected to fill in the `std::string Decoder::decode(const std::string&)` function. Good luck! General Patron is counting on you!

### Solution

**Code:**

```cpp
#include <cmath>
#include <unordered_map>

struct Decoder {
  static std::unordered_map<char, char> forward_map;
  static std::unordered_map<char, char> reverse_map;

  static void build_maps(const std::string& input) {
    std::string current_encoded;
    for (std::size_t i = 0; i < input.length(); ++i) {
        char current_char = input[i];

        // Encode the character position + 1 times
        for (std::size_t j = 0; j <= i; ++j) {
            current_encoded = Encoder::encode(std::string(1, current_char));
            forward_map[current_char] = current_encoded[0];
            reverse_map[current_encoded[0]] = current_char;
            current_char = current_encoded[0];
        }
    }
  }

  static char decode_char(char ch, std::size_t position) {
    char current_char = ch;
    for (std::size_t i = 0; i <= position; ++i) {
        current_char = reverse_map[current_char];
    }
    return current_char;
  }

  static std::string decode(const std::string& p_what) {  
    std::string test_input = "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa!@#$%^&*()_+-";
    build_maps(test_input);

    std::string result = "";
    for(size_t i = 0; i < p_what.size(); i++){
      result.push_back(decode_char(p_what[i],i));
    }

    return result;
  }
};

// Define the static members outside the class
std::unordered_map<char, char> Decoder::forward_map;
std::unordered_map<char, char> Decoder::reverse_map;
```

**Explanation:**

The solution revolves around understanding the relationship between characters and their position in the encoded string. The `build_maps` function constructs two maps: `forward_map` and `reverse_map`. The former maps characters to their encoded counterpart, while the latter does the reverse. The logic is to encode each character in the string multiple times based on its position and update the maps accordingly. To decode, we reverse the process: for each character in the encoded string, we repeatedly look it up in the `reverse_map` based on its position.

### Key Concepts

- `std::unordered_map`: A container that stores elements in key-value pairs, where the key values are unique and hashable. It provides constant time average complexity for most operations.
- `std::string::length()`: Returns the number of characters in the string.
- `std::size_t`: An unsigned integral data type used to represent sizes.

### Tags

- #std/unordered_map
- #std/string
- #data-structures
- #encoding
- #decoding

---

## alternate solution

```C++
struct Decoder {
	static std::string decode (const std::string& p_what) {  
    std::string key = std::string("aHqPuRvkM07DoO1AU49EW5CVxlfcIY6.? GXyTwS3BngKZzmNtjeJriLsQ28,Fphdb");
    
    std::string result = std::string("");
    for (const char &c : p_what) {
       int index = key.find(c);
       result += (index!=std::string::npos) ? key[(index + result.size() + 1) % key.size()] : c;
    }

    return result;
	}
};
```

