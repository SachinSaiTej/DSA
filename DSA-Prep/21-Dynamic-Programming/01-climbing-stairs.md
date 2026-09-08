# Climbing Stairs

## Problem
Count the distinct ways to reach stair `n` when each move is 1 or 2 stairs.

## Intuition
The final step comes from either `n-1` or `n-2`, so `ways[n] = ways[n-1] + ways[n-2]`.

## Java
```java
public int climbStairs(int n) {
    if (n <= 2) return n;
    int a=1,b=2;
    for(int i=3;i<=n;i++){ int c=a+b; a=b; b=c; }
    return b;
}
```

## Complexity
Time O(n), space O(1).