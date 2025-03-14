# 155: Min Stack - Solution Approach

## Problem Understanding 🤔

To implement a stack that can retrieve the minimum element in constant time, we need an auxiliary stack (minStack) that keeps track of the minimum elements alongside our main stack. This approach ensures O(1) time complexity for all operations.

## Solution Approach 🎯

The solution uses two stacks:

- Main stack (obj): Stores all the elements
- Minimum stack (minStack): Maintains the minimum elements seen so far

## Complete Implementation💻

```java
import java.util.Stack;

public class Main {
    class MinStack {
        private Stack<Integer> obj;
        private Stack<Integer> minStack;
        
        public MinStack() {
            obj = new Stack<>();
            minStack = new Stack<>();
        }
        
        public void push(int val) {
            obj.push(val);
            if (minStack.isEmpty() || val <= minStack.peek()) {
                minStack.push(val);
            }
        }
        
        public void pop() {
            if (obj.pop().equals(minStack.peek())) {
                minStack.pop();
            }
        }
        
        public int top() {
            return obj.peek();
        }
        
        public int getMin() {
            return minStack.peek();
        }
    }

    public static void main(String[] args) {
        MinStack minStack = new Main().new MinStack();
        minStack.push(-2);
        minStack.push(0);
        minStack.push(-3);
        System.out.println(minStack.getMin()); // returns -3
        minStack.pop();
        System.out.println(minStack.top());    // returns 0
        System.out.println(minStack.getMin()); // returns -2
    }
}
```

## Complexity Analysis⚡

**Time Complexity:**

- Push: O(1)
- Pop: O(1)
- Top: O(1)
- getMin: O(1)

**Space Complexity:** O(n)

Where n is the number of elements in the stack. In worst case, if elements are pushed in descending order, minStack will contain all elements.

## Key Points💡

- The minStack only stores elements when they are smaller than or equal to the current minimum
- Using equals() instead of == for comparison ensures proper object comparison
- The auxiliary stack approach trades space for constant-time minimum element retrieval