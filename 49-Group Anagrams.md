# 49: Group Anagrams - Solution Approach

## Problem Understanding🤔

Given an array of strings, we need to group all anagrams together. Strings that are anagrams of each other should be grouped in the same list.

## Solution Approach🎯

We can solve this using a HashMap-based approach where:

- For each string, we create a sorted version as the key
- Group original strings with the same sorted version together
- Return all groups as a list

## Code Implementation💻

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        
        for(String str : strs) {
            char[] chars = str.toCharArray();
            Arrays.sort(chars);
            String sortedStr = new String(chars);
            
            if(!map.containsKey(sortedStr)) {
                map.put(sortedStr, new ArrayList<>());
            }
            map.get(sortedStr).add(str);
        }
        return new ArrayList<>(map.values());
    }
}
```

## Example Walkthrough

For input: ["eat","tea","tan","ate","nat","bat"]

- First iteration: "eat" → sorted "aet" → create new list → add "eat"
- Second iteration: "tea" → sorted "aet" → add to existing list → ["eat","tea"]
- Third iteration: "tan" → sorted "ant" → create new list → add "tan"
- And so on...

## How It Works

The solution works by using sorted strings as keys in a HashMap:

- Converting each string to a char array allows us to sort the characters
- The sorted string becomes our key, ensuring all anagrams map to the same key
- We maintain lists of original strings as values in the map
- Finally, we collect all the lists of anagrams and return them

## Time and Space Complexity⚡

- Time Complexity: O(N * K * log K) where N is the length of input array and K is the maximum length of a string
- Space Complexity: O(N * K) to store all strings in the HashMap