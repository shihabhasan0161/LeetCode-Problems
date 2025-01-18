# 271: Encode and Decode Strings - Solution Approach

## Problem Overview🤔

Design an algorithm to encode a list of strings into a single string, and decode it back to the original list of strings.

## Solution Approach🎯

The key idea is to store each string's length before the actual string content. This creates a delimiter-based approach that can handle any characters in the strings.

### Encoding Process💡

- For each string in the input list:
    - Convert the length of the string to a character
    - Append this length character to the result
    - Append the actual string content

### Decoding Process💡

- Iterate through the encoded string:
    - Read the first character to get the length of the next string
    - Extract the substring of that length
    - Add it to the result list
    - Move the pointer past the extracted string

## Coding Implementation💻

```java
class Solution {

    public String encode(List<String> strs) {
        StringBuilder encodedString = new StringBuilder();

        for(String str : strs) {
            encodedString.append((char) str.length()).append(str);
        } return encodedString.toString();
    }

    public List<String> decode(String str) {
        List<String> decodedString = new ArrayList<>();

        int i = 0;
        while(i < str.length()) {
            int size = str.charAt(i++);
            decodedString.add(str.substring(i, i+size));
            i+=size;
        }
        return decodedString;
    }
}
```

## Time Complexity⚡

- Encode: O(n), where n is the total length of all strings
- Decode: O(n), where n is the length of the encoded string

## Space Complexity🚀

O(n) for both encode and decode operations, where n is the total length of all strings

## Key Points🌟

- The solution uses the character representation of string lengths as delimiters
- It can handle strings containing any UTF-8 characters
- No special delimiter character is needed, making it efficient and robust
- The approach works because we store the length information separately from the content