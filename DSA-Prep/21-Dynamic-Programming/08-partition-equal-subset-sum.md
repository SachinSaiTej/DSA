# Partition Equal Subset Sum

## Problem
Determine whether an array can be split into two subsets with equal sum.

## Intuition
If total sum is odd, impossible. Otherwise ask whether a subset can make `sum/2`; this is 0/1 knapsack with boolean state.

## Java
```java
public boolean canPartition(int[]a){int sum=0;for(int x:a)sum+=x;if((sum&1)==1)return false;int t=sum/2;boolean[]dp=new boolean[t+1];dp[0]=true;for(int x:a)for(int s=t;s>=x;s--)dp[s]|=dp[s-x];return dp[t];}
```

## Complexity
Time O(n·sum), space O(sum).