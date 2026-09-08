# Redundant Connection

## Problem
Find an edge that can be removed so an undirected graph becomes a tree.

## Intuition
Process edges with DSU. The first edge whose endpoints are already connected is redundant.

## Java
```java
public int[] findRedundantConnection(int[][]e){DSU d=new DSU(e.length+1);for(int[]x:e)if(!d.union(x[0],x[1]))return x;return new int[0];}
static class DSU{int[]p;DSU(int n){p=new int[n];for(int i=0;i<n;i++)p[i]=i;}int f(int x){return p[x]==x?x:(p[x]=f(p[x]));}boolean union(int a,int b){a=f(a);b=f(b);if(a==b)return false;p[a]=b;return true;}}
```

## Complexity
Time O(E α(V)), space O(V).