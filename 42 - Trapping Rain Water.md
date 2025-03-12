# 42: Trapping Rain Water - Solution Approach

## Problem Understanding 🤔

Given an array of non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

## Solution Approach: Two Pointers🎯

We use a two-pointer approach to solve this problem efficiently with O(n) time complexity and O(1) space complexity.

### Key Concepts

- Use two pointers: left and right
- Track maximum height seen from left and right
- Compare leftMax and rightMax to determine which pointer to move
- Calculate trapped water at each position

### Algorithm Steps

1. Initialize pointers: left at 1 and right at length-2
2. Track leftMax starting from height[0] and rightMax from height[length-1]
3. While left ≤ right:
    - If rightMax ≤ leftMax:
        
        - Update rightMax
        
        - Calculate water trapped at right position
        
        - Move right pointer left
        
    - Else:
        
        - Update leftMax
        
        - Calculate water trapped at left position
        
        - Move left pointer right
        

### Coding Implementation💻

```java
public class Solution {
    static int trap(int[] height) {
        int right = height.length - 2;
        int left = 1;
        int leftMax = height[left-1];
        int rightMax = height[right+1];
        int res = 0;
        
        while (left <= right) {
            if(rightMax <= leftMax) {
                rightMax = Math.max(rightMax, height[right]);
                res += Math.max(0, rightMax - height[right]);
                right--;
            } else {
                leftMax = Math.max(leftMax, height[left]);
                res += Math.max(0, leftMax - height[left]);
                left++;
            }
        }
        return res;
    }
}

```

## Time and Space Complexity⚡

- Time Complexity: O(n) - we traverse the array once
- Space Complexity: O(1) - we only use constant extra space

## Example

Input: height = [4,2,0,3,2,5]

Output: 9

Explanation: Water accumulates between the bars as follows:

- Between index 1 and 3: 2 units
- Between index 2 and 3: 3 units
- Between index 3 and 5: 4 units

Total trapped water = 9 units