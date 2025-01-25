# 167: Two Sum II - Solution Approach

## Problem Overview🤔

Given a 1-indexed sorted array of integers, find two numbers that add up to a specific target. Return the indices of these numbers, added by one.

## Key Points💡

- The input array is sorted in non-decreasing order
- Array is 1-indexed
- Exactly one solution exists
- Same element cannot be used twice

## Solution Approach: Two Pointers🎯

We can solve this efficiently using the two pointers technique:

- Initialize two pointers: left at the start (index 0) and right at the end of array
- While left pointer is less than right pointer:
    - If sum of numbers at left and right is greater than target, decrease right pointer
    - If sum is less than target, increase left pointer
    - If sum equals target, return indices (added by 1)

## Code Implementation💻

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int left = 0;
        int right = numbers.length-1;
        
        while (left < right) {
            if(numbers[left] + numbers[right] > target) {
                right--;
            } else if (numbers[left] + numbers[right] < target) {
                left++;
            } else {
                return new int[] {left+1, right+1};
            }
        }
        return new int[]{};
    }
}
```

## Time and Space Complexity⚡

- Time Complexity: O(n) - we traverse the array once
- Space Complexity: O(1) - we only use two pointers

## Why This Works

This approach works because the array is sorted. When the sum is too large, we know we need a smaller number, so we move the right pointer left. When the sum is too small, we need a larger number, so we move the left pointer right. This guarantees we'll find the solution if it exists.