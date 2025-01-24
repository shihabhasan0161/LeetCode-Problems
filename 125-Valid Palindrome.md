# 125: Valid Palindrome - Solution Approach

## Problem Overview🤔

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

## Solution Approach🎯

We use string manipulation and comparison to check for palindromes:

- Convert the string to lowercase to make case-insensitive comparison
- Remove all non-alphanumeric characters using regex
- Create a reversed version of the cleaned string
- Compare the cleaned string with its reverse

## Code Implementation💻

```java
class Solution {
    public boolean isPalindrome(String s) {
        s = s.toLowerCase().replaceAll("[^a-zA-Z0-9]", "");
        String revString = "";
        for(int i=s.length()-1; i>=0; i--) {
            revString = revString + s.charAt(i);
        }
        return s.equals(revString);
    }
}
```

## Time and Space Complexity⚡

- Time Complexity: O(n) - where n is the length of the string
- Space Complexity: O(n) - we create a new string for the reversed version

## Key Insights💡

- toLowerCase() handles case sensitivity
- replaceAll("[^a-zA-Z0-9]", "") removes all non-alphanumeric characters
- String comparison with equals() checks if the string matches its reverse

## Example

For input "A man, a plan, a canal: Panama":

- After lowercase: "a man, a plan, a canal: panama"
- After cleaning: "amanaplanacanalpanama"
- Reverse string: "amanaplanacanalpanama"
- Both strings match → return true