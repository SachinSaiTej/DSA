# Jump Game II

## Problem
Find the minimum number of jumps needed to reach the last index.

## Intuition
Treat each jump as a level. While scanning the current range, compute the farthest next range. When the current range ends, make the next jump.

## Java
```java
public int jump(int[] nums) {
    int jumps = 0, end = 0, farthest = 0;
    for (int i = 0; i < nums.length - 1; i++) {
        farthest = Math.max(farthest, i + nums[i]);
        if (i == end) { jumps++; end = farthest; }
    }
    return jumps;
}
```

## Complexity
Time O(n), space O(1).