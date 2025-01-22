# 238: Product of Array Except Self - Solution Approach

## Problem Understanding🤔

Given an array nums, we need to return an array answer where answer[i] equals the product of all elements in nums except nums[i]. The solution must run in O(n) time without using division operation.

## Key Constraints

- Array length is between 2 and 10^5
- Elements range from -30 to 30
- The product of any prefix or suffix fits in a 32-bit integer
- Must solve without using division
- Time complexity must be O(n)

## Solution Approach🎯

The solution uses a prefix and suffix product approach:

### 1. Prefix Products

- Initialize result array and prefix variable to 1
- Iterate left to right through the array
- At each index i, store the product of all numbers to the left
- Update prefix by multiplying it with the current number

### 2. Suffix Products

- Initialize suffix variable to 1
- Iterate right to left through the array
- Multiply each position with suffix (product of all numbers to the right)
- Update suffix by multiplying it with the current number

## Example Walkthrough

For array [1,2,3,4]:

- First pass (prefix products):
    - result = [1,1,2,6]
- Second pass (multiply with suffix products):
    - result = [24,12,8,6]

## Code Implementation💻

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int[] result = new int[nums.length];
        int prefix = 1;
        for(int i = 0; i < nums.length; i++) {
            result[i] = prefix;
            prefix *= nums[i];
        }

        int suffix = 1;
        for(int i = nums.length-1; i >= 0; i--) {
            result[i] *= suffix;
            suffix *= nums[i];
        }

        return result;
    }
}
```

## Time and Space Complexity⚡

Time Complexity: O(n) - Two passes through the array

Space Complexity: O(1) - Only using the output array, which doesn't count as extra space

## Key Insights💡

- The solution avoids division by using prefix and suffix products
- Each element in the final array is the product of all numbers to its left multiplied by all numbers to its right
- The approach is space-efficient as it uses only the output array
- Two passes through the array are sufficient to compute all required products