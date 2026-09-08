# Daily Temperatures

## Problem
For each temperature, find how many days you must wait for a warmer temperature.

## Intuition
Use a monotonic decreasing stack of indices. When a warmer temperature arrives, resolve all colder indices on top.

## Java
```java
public int[] dailyTemperatures(int[] t) {
    int[] ans = new int[t.length];
    Deque<Integer> stack = new ArrayDeque<>();
    for (int i = 0; i < t.length; i++) {
        while (!stack.isEmpty() && t[i] > t[stack.peek()]) {
            int j = stack.pop();
            ans[j] = i - j;
        }
        stack.push(i);
    }
    return ans;
}
```

## Complexity
Time O(n), space O(n).