# 217: Contains Duplicate - Solution Approach

## Problem Statement🤔

Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

## Solution Approach🎯

Let's break down a simple and efficient solution using the sorting approach:

### Algorithm Steps

- Sort the input array in ascending order
- Iterate through the sorted array
- Compare adjacent elements
- If any adjacent elements are equal, return true
- If no duplicates found, return false

### Code Implementation**💻**

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums);
        
        for(int i = 0; i < nums.length-1; i++) {
            if(nums[i] == nums[i+1]) {
                return true;
            }
        }
        return false;
    }
}
```

### How It Works

Let's use an example to understand the solution:

Input array: [1, 2, 3, 1]

- After sorting: [1, 1, 2, 3]
- First comparison: nums[0] == nums[1] (1 == 1) → true
- Return true as we found a duplicate

### Time and Space Complexity⚡

- Time Complexity: O(n log n) due to sorting
- Space Complexity: O(1) as we're not using any extra space

### Key Points 💡

- Sorting makes duplicate elements adjacent to each other
- We only need one pass through the array after sorting
- The solution handles both positive and negative integers

This approach is memory efficient but trades off some time complexity due to sorting. For cases where memory isn't a constraint, using a HashSet would provide O(n) time complexity.