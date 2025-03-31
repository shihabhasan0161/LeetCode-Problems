# 150: Evaluate Reverse Polish Notation - Solution Approach

## Problem Understanding🤔

Evaluate an arithmetic expression in Reverse Polish Notation (RPN). The expression is represented as an array of strings where each element is either an operator (+, -, *, /) or an operand (number).

## Solution Approach🎯

We can solve this problem using a stack-based approach:

- Initialize an empty stack to store numbers
- Iterate through each token in the input array
- If the token is a number, push it onto the stack
- If the token is an operator, pop two numbers from the stack, apply the operator, and push the result back

## Coding Implementation💻

```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack<>();
        
        for(String c : tokens) {
            if(c.equals("+")) {
                stack.push(stack.pop() + stack.pop());
            } else if (c.equals("-")) {
                int second = stack.pop();
                int first = stack.pop();
                stack.push(first - second);
            } else if(c.equals("*")) {
                stack.push(stack.pop() * stack.pop());
            } else if(c.equals("/")) {
                int second = stack.pop();
                int first = stack.pop();
                stack.push(first / second);
            } else {
                stack.push(Integer.parseInt(c));
            }
        }
        return stack.peek();
    }
}

```

## Time and Space Complexity⚡

- **Time Complexity:** O(n) where n is the length of the input array
- **Space Complexity:** O(n) for the stack storage

## Key Points💡

- For subtraction and division, order matters! Pop the second operand first, then the first operand
- The input is guaranteed to be a valid RPN expression
- Division between two integers truncates toward zero
- All intermediate results fit in a 32-bit integer

## Example Walkthrough

For input ["2", "1", "+", "3", "*"]:

1. Push 2: stack = [2]
2. Push 1: stack = [2, 1]
3. '+': Pop twice (1, 2), add them (2+1=3), push result: stack = [3]
4. Push 3: stack = [3, 3]
5. '*': Pop twice (3, 3), multiply them (3*3=9), push result: stack = [9]

Final result: 9