# House Robber

## Problem
Maximize money robbed from houses when adjacent houses cannot both be robbed.

## Intuition
At each house choose skip it or rob it. Keep only the best values for the previous two positions.

## Java
```java
public int rob(int[] nums) {
    int prev2=0, prev1=0;
    for(int x:nums){ int cur=Math.max(prev1,prev2+x); prev2=prev1; prev1=cur; }
    return prev1;
}
```

## Complexity
Time O(n), space O(1).