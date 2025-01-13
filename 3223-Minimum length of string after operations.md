# 3223: Minimum Length of String After Operations - Solution Approach

## Problem Understanding🤔

We need to find the minimum possible length of a string after performing a series of operations. In each operation, we:

- Choose an index i where there is at least one matching character to its left and right
- Delete the closest matching character to the left
- Delete the closest matching character to the right

## Solution Approach🎯

The key insight is to count the frequency of each character and determine the minimum number of characters that must remain after all possible operations.

### Algorithm Steps

- Create a frequency array to count occurrences of each character
- For each character frequency:
- If frequency is even, we need to keep 2 characters
- If frequency is odd, we need to keep 1 character

### **Code Implementation 💻**

```java
class Solution {
    public int minimumLength(String s) {
        int[] freq = new int[26];
        for(int i = 0; i < s.length(); i++) {
            freq[s.charAt(i) - 'a']++;
        }
        int deleteCount = 0;

        for(int frequency : freq) {
            if(frequency == 0) continue;
            if(frequency % 2 == 0) {
                deleteCount += 2;
            } else {
                deleteCount += 1;
            }
        }
        return deleteCount;
    }
}
```

## Time & Space Complexity⚡

- Time Complexity: O(n) where n is the length of the input string
- Space Complexity: O(1) as we use a fixed-size array of 26 characters

## Example

For input string "abaacbcbb":

- Frequency count: a:3, b:4, c:2
- For 'a' (odd count): keep 1
- For 'b' (even count): keep 2
- For 'c' (even count): keep 2

Total minimum length = 1 + 2 + 2 = 5