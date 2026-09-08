# Unique Paths

## Problem
Count paths from the top-left to bottom-right of an `m × n` grid when movement is only right or down.

## Intuition
The number of ways to a cell is the sum of ways to the cell above and the cell to the left.

## Java
```java
public int uniquePaths(int m,int n){int[]dp=new int[n];Arrays.fill(dp,1);for(int r=1;r<m;r++)for(int c=1;c<n;c++)dp[c]+=dp[c-1];return dp[n-1];}
```

## Complexity
Time O(mn), space O(n).