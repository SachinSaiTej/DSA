# Largest Rectangle in Histogram

## Problem
Find the largest rectangle area that can be formed from histogram bars.

## Intuition
Maintain an increasing stack of indices. When a lower bar appears, pop bars and use the current index as their right boundary.

## Java
```java
public int largestRectangleArea(int[] h) {
    Deque<Integer> st = new ArrayDeque<>();
    int best = 0;
    for (int i = 0; i <= h.length; i++) {
        int cur = (i == h.length) ? 0 : h[i];
        while (!st.isEmpty() && cur < h[st.peek()]) {
            int height = h[st.pop()];
            int left = st.isEmpty() ? -1 : st.peek();
            best = Math.max(best, height * (i - left - 1));
        }
        st.push(i);
    }
    return best;
}
```

## Complexity
Time O(n), space O(n).