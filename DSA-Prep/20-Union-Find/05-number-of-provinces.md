# Number of Provinces

## Problem
Given an adjacency matrix representing cities connected by roads, count connected groups of cities.

## Intuition
Initially every city is its own province. Union every connected pair and count distinct roots.

## Java
```java
public int findCircleNum(int[][]is){int n=is.length;DSU d=new DSU(n);int c=n;for(int i=0;i<n;i++)for(int j=i+1;j<n;j++)if(is[i][j]==1&&d.union(i,j))c--;return c;}
static class DSU{int[]p;DSU(int n){p=new int[n];for(int i=0;i<n;i++)p[i]=i;}int f(int x){return p[x]==x?x:(p[x]=f(p[x]));}boolean union(int a,int b){a=f(a);b=f(b);if(a==b)return false;p[a]=b;return true;}}
```

## Complexity
Time O(n² α(n)), space O(n).