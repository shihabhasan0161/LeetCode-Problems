# 2116-Check if a parentheses string can be valid - Solution Approach

## Problem Understanding🤔

The problem asks us to determine if a string of parentheses can be made valid by modifying certain positions. Each character in the string is either locked (cannot be changed) or unlocked (can be changed to either '(' or ')').

## Key Insights💡

- If the string length is odd, it's impossible to make it valid
- For a parentheses string to be valid, we need to ensure:
    - At any point reading left to right, we can't have more closing parentheses than opening ones
    - At any point reading right to left, we can't have more opening parentheses than closing ones
    - The final number of opening and closing parentheses must be equal

## Solution Approach🎯

The solution uses a two-pass approach:

### First Pass (Left to Right)

- Keep track of two variables:
    - `balance`: counts the difference between opening and closing parentheses
    - `available`: counts the number of positions we can modify
- For each position:
    - If it's unlocked (`locked[i] == '0'`), increment available
    - If it's a locked opening parenthesis, increment balance
    - If it's a locked closing parenthesis, decrement balance
- At any point, if `balance + available < 0`, return false

### Second Pass (Right to Left)

Similar to the first pass, but reading from right to left and considering closing parentheses as positive balance.

## Tips and Tricks🌟

- Always check for odd length strings first - they can never be valid
- The two-pass approach helps verify both conditions:
    - First pass ensures we never have too many closing parentheses
    - Second pass ensures we never have too many opening parentheses
- The `balance + available` check is crucial - it represents whether we can potentially fix any imbalance using available positions

## Code Implementation 💻

```java
class Solution {
    public boolean canBeValid(String s, String locked) {
        if(s.length() % 2 != 0) {
            return false;
        }
        int balance = 0;
        int available = 0;
        for(int i = 0; i<s.length(); i++) {
            if(locked.charAt(i) == '0'){
                available++;
            } else if(s.charAt(i) == '(') {
                balance++;
            } else {
                balance--;
            }
            if(balance+available <0){
                return false;
            }
        }
        balance = 0;
        available = 0;

        for(int i = s.length()-1; i>=0; i--) {
            if(locked.charAt(i) == '0') {
                available++;
            } else if(s.charAt(i) == ')') {
                balance++;
            } else {
                balance--;
            }
            if(balance+available <0){
                return false;
            }
        }
        return true;
    }
}
```

## Time and Space Complexity⚡

- Time Complexity: O(n) where n is the length of the string
- Space Complexity: O(1) as we only use constant extra space