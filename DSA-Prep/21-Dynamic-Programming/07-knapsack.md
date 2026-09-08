# 0/1 Knapsack

## Problem
Maximize total value when each item can be selected at most once and the total weight cannot exceed capacity.

## Intuition
`dp[w]` stores the best value for capacity `w`. Traverse capacities backward so an item cannot be used more than once.

## Java
```java
public int knapsack(int[]wt,int[]val,int cap){int[]dp=new int[cap+1];for(int i=0;i<wt.length;i++)for(int w=cap;w>=wt[i];w--)dp[w]=Math.max(dp[w],dp[w-wt[i]]+val[i]);return dp[cap];}
```

## Complexity
Time O(n·capacity), space O(capacity).