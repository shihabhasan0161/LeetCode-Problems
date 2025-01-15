# 242: Valid Anagram - Solution Approach

## Problem Understanding🤔

Given two strings s and t, we need to determine if t is an anagram of s. An anagram is a word formed by rearranging the letters of another word, using all the original letters exactly once.

## Solution Approach🎯

We can solve this problem using a sorting-based approach:

- Convert both strings to character arrays for easier manipulation
- Sort both character arrays
- Compare the sorted arrays for equality

## Code Implementation **💻**

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        char tempS[] = s.toCharArray();
        char tempT[] = t.toCharArray();
        Arrays.sort(tempS);
        Arrays.sort(tempT);

        return Arrays.equals(tempS, tempT);
    }
}
```

## Example Walkthrough

For input: s = "anagram", t = "nagaram"

- Convert to char arrays: ['a','n','a','g','r','a','m'] and ['n','a','g','a','r','a','m']
- After sorting: ['a','a','a','g','m','n','r'] and ['a','a','a','g','m','n','r']
- Arrays are equal → return true

## Why This Works

This solution works because anagrams contain exactly the same characters with the same frequency. When we sort both strings, they should become identical if they are anagrams. The Arrays.equals() method then simply verifies this equality.

## Time and Space Complexity⚡

- Time Complexity: O(n log n) due to the sorting operation
- Space Complexity: O(n) where n is the length of the input strings