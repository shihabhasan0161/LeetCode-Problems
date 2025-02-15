# 11. Container With Most Water - Solution Approach

## Problem Understanding🤔

Given an array height where height[i] represents the height of a vertical line at position i, find two lines that together with the x-axis forms a container that can hold the most water.

## Key Insights💡

- Use two pointers technique (left and right) to find the maximum area
- Area is calculated by: width (distance between lines) × height (minimum of two line heights)
- Move the pointer with smaller height inward to potentially find a larger area

## Solution Approach🎯

The solution uses a two-pointer approach:

- Initialize left pointer at start (0) and right pointer at end (length-1)
- Calculate current area using min(height[left], height[right]) × (right-left)
- Update maximum area if current area is larger
- Move the pointer with smaller height inward (if equal, move either one)

## Code Implementation💻

**Java Solution:**

```java
class Solution {
    public int maxArea(int[] height) {
        int res = 0;
        int left = 0;
        int right = height.length-1;
        while(left < right){
            res = Math.max(res,Math.min(height[left], height[right]) * (right-left));
            if(height[left] <= height[right]){
                left++;
            } else {
                right--;
            }
        }
        return res;
    }
}
```

**JavaScript Solution:**

```jsx
var maxArea = function(height) {
    var res = 0;
    var l = 0;
    var r = height.length-1;
    while(l<r){
        res = Math.max(res, Math.min(height[l], height[r]) * (r-l));
        if(height[l] <= height[r]){
            l++;
        } else{
            r--;
        }
    }
    return res;
};
```

**Python Solution:**

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        res = 0
        l = 0
        r = len(height)-1
        
        while l<r:
            res = max(res, min(height[l], height[r]) * (r-l))
            if(height[l] <= height[r]):
                l+=1
            else:
                r-=1
        return res
```

## Time and Space Complexity⚡

- Time Complexity: O(n) - single pass through the array
- Space Complexity: O(1) - only using two pointers