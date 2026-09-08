# Jump Game

## Problem
Determine whether you can reach the last index when `nums[i]` gives the maximum jump length from index i.

## Intuition
Track the farthest reachable index. If the current index ever exceeds it, the end is unreachable.

## Java
```java
public boolean canJump(int[] nums) {
    int farthest = 0;
    for (int i = 0; i < nums.length; i++) {
        if (i > farthest) return false;
        farthest = Math.max(farthest, i + nums[i]);
    }
    return true;
}
```

## Complexity
Time O(n), space O(1).