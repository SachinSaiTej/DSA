# Difference Array

## Intuition
For range additions, store only boundary changes: `diff[l] += x` and `diff[r+1] -= x`. Prefix-summing the difference array applies all updates.

## Java
```java
public int[] applyRangeUpdates(int n,int[][] updates){int[] d=new int[n+1];for(int[] u:updates){d[u[0]]+=u[2];if(u[1]+1<n)d[u[1]+1]-=u[2];}int[] a=new int[n];for(int i=0,cur=0;i<n;i++){cur+=d[i];a[i]=cur;}return a;}
```

## Complexity
O(n + updates) time, O(n) space.