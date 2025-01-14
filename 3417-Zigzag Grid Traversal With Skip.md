# 3417: Zigzag Grid Traversal With Skip - Solution Approach

## Problem Understanding🤔

Given an m x n 2D array of positive integers, we need to:

- Traverse the grid in a zigzag pattern
- Skip alternate cells during traversal
- Return an array containing the visited cell values in order

## Key Points 👨‍💻

- Start from top-left cell (0,0)
- Move right in first row, then left in second row (zigzag pattern)
- Only visit cells where (i + j) % 2 == 0
- Continue alternating between right and left traversal for each row

## Solution Approach🎯

The solution uses these key strategies:

- Use a boolean flag leftToRight to track direction
- Iterate through each row of the grid
- For each row, traverse either left-to-right or right-to-left based on flag
- Only add cells that satisfy the alternate condition using modulo

## Code Implementation**💻**

```java
class Solution {
    public List<Integer> zigzagTraversal(int[][] grid) {
        List<Integer> newList = new ArrayList<>();
        boolean leftToRight = true;
        
        for(int i = 0; i < grid.length; i++) {
            if(leftToRight) {
                for(int j = 0; j < grid[0].length; j++) {
                    if((i + j) % 2 == 0) {
                        newList.add(grid[i][j]);
                    }
                }
            } else {
                for(int j = grid[i].length-1; j >= 0; j--) {
                    if((i + j) % 2 == 0) {
                        newList.add(grid[i][j]);
                    }
                }
            }
            leftToRight = !leftToRight;
        }
        return newList;
    }
}
```

## Time & Space Complexity⚡

**Time Complexity:** O(m*n) where m is number of rows and n is number of columns

**Space Complexity:** O(k) where k is the number of cells that satisfy the alternate condition

## Example Walkthrough

For input grid = [[1,2],[3,4]]:

- Start at (0,0): Add 1
- Skip (0,1) due to alternate condition
- Move to second row, going right to left
- Skip (1,0) due to alternate condition
- Add 4 at (1,1)

Final output: [1,4]