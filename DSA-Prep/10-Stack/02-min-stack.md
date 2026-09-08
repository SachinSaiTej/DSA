# Min Stack

## Problem
Design a stack supporting `push`, `pop`, `top`, and retrieving the minimum value in O(1).

## Intuition
Store the current minimum alongside each value. Every stack entry therefore knows the minimum value from the bottom up to that entry.

## Java
```java
class MinStack {
    private final Deque<int[]> stack = new ArrayDeque<>();

    public void push(int val) {
        int min = stack.isEmpty()
                ? val
                : Math.min(val, stack.peek()[1]);

        stack.push(new int[]{val, min});
    }

    public void pop() {
        stack.pop();
    }

    public int top() {
        return stack.peek()[0];
    }

    public int getMin() {
        return stack.peek()[1];
    }
}
```

## Complexity
All operations O(1), space O(n).