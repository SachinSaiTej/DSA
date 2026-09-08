# Largest Rectangle in Histogram

## Problem
Find the largest rectangle area that can be formed from histogram bars.

## Intuition
Maintain an increasing stack of indices. When a lower bar appears, pop bars and use the current index as their right boundary.

## Java
```java
public int largestRectangleArea(int[] heights) {
    Deque<Integer> stack = new ArrayDeque<>();
    int best = 0;

    for (int i = 0; i <= heights.length; i++) {
        int currentHeight = (i == heights.length) ? 0 : heights[i];

        while (!stack.isEmpty() && currentHeight < heights[stack.peek()]) {
            int height = heights[stack.pop()];
            int leftBoundary = stack.isEmpty() ? -1 : stack.peek();
            int width = i - leftBoundary - 1;
            best = Math.max(best, height * width);
        }

        stack.push(i);
    }

    return best;
}
```

## Complexity
Time O(n), space O(n).