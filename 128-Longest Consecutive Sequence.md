# 128: Longest Consecutive Sequence - Solution Approach

## Problem Overview🤔

Given an unsorted array of integers, find the length of the longest consecutive sequence of numbers.

## Solution Approach🎯

We use a HashSet to efficiently find consecutive elements:

- First, add all numbers to a HashSet for O(1) lookups
- For each number n in the set, check if it's the start of a sequence by verifying n-1 doesn't exist
- If it's a sequence start, count consecutive numbers (n+1, n+2, etc.) until the sequence breaks
- Keep track of the maximum sequence length found so far

## Code Implementation💻

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        Set<Integer> store = new HashSet<>();
        int res = 0;
        
        // Add all numbers to HashSet
        for(int n : nums) {
            store.add(n);
        }
        
        // Check each potential sequence
        for(int n : store) {
            if(!store.contains(n-1)) {
                int count = 0;
                while(store.contains(n+count)) {
                    count++;
                }
                res = Math.max(res, count);
            }
        }
        return res;
    }
}
```

## Time and Space Complexity⚡

- Time Complexity: O(n) - we iterate through the array twice at most
- Space Complexity: O(n) - we store all numbers in a HashSet

## Key Insights💡

- Using a HashSet gives us O(1) lookup time for checking consecutive numbers
- We only start counting sequences from their first number (when n-1 doesn't exist)
- This prevents counting the same sequence multiple times

## Example

For input [100,4,200,1,3,2]:

- The HashSet contains: {1,2,3,4,100,200}
- When n=1: count consecutive numbers (1,2,3,4) → length 4
- When n=100: count (100) → length 1
- When n=200: count (200) → length 1

The longest sequence is [1,2,3,4], so return 4