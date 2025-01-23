# 36: Valid Sudoku - Solution Approach

## Problem Overview🤔

Determine if a partially filled 9x9 Sudoku board is valid according to these rules:

- Each row must contain digits 1-9 without repetition
- Each column must contain digits 1-9 without repetition
- Each 3x3 sub-box must contain digits 1-9 without repetition

## Solution Approach🎯

We use HashMaps and HashSets to track numbers in each row, column, and 3x3 sub-box:

- Create three HashMaps to store sets for rows, columns, and 3x3 squares
- Iterate through each cell in the 9x9 board
- For each filled cell (non-'.'), check if the number already exists in its respective row, column, or square
- Use (r/3, c/3) coordinates to identify which 3x3 square the current cell belongs to

## Code Implementation💻

```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        Map<Integer, Set<Character>> col = new HashMap<>();
        Map<Integer, Set<Character>> row = new HashMap<>();
        Map<String, Set<Character>> square = new HashMap<>();

        for(int r = 0; r < 9; r++) {
            for(int c = 0; c < 9; c++) {
                if(board[r][c] == '.') continue;
                String squareString = (r/3) + "," + (c/3);

                if(row.computeIfAbsent(r, k -> new HashSet<>()).contains(board[r][c]) || 
                col.computeIfAbsent(c, k -> new HashSet<>()).contains(board[r][c]) || 
                square.computeIfAbsent(squareString, k -> new HashSet<>()).contains(board[r][c])) {
                    return false;
                }
                row.get(r).add(board[r][c]);
                col.get(c).add(board[r][c]);
                square.get(squareString).add(board[r][c]);
            }
        } return true;
    }
}
```

## Time and Space Complexity⚡

- Time Complexity: O(1) since we're always iterating through a 9x9 board
- Space Complexity: O(1) since we store at most 9 digits for each row, column, and square

## Common Pitfalls

- Forgetting to check empty cells (marked as '.')
- Incorrect calculation of 3x3 square coordinates
- Not using HashSet's contains() method to check for duplicates

## Tips

- Use computeIfAbsent() to create new HashSets when needed
- Create a unique string key for each 3x3 square using row/3 and col/3
- Skip validation for empty cells to improve efficiency