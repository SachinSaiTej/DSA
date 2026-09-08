# Number of Connected Components

## Problem
Count connected components in an undirected graph.

## Intuition
Union the endpoints of every edge. Each successful union reduces the number of components by one.

## Java
```java
public int countComponents(int n,int[][]e){DSU d=new DSU(n);int c=n;for(int[]x:e)if(d.union(x[0],x[1]))c--;return c;}
static class DSU{int[]p,sz;DSU(int n){p=new int[n];sz=new int[n];for(int i=0;i<n;i++){p[i]=i;sz[i]=1;}}int find(int x){return p[x]==x?x:(p[x]=find(p[x]));}boolean union(int a,int b){a=find(a);b=find(b);if(a==b)return false;if(sz[a]<sz[b]){int t=a;a=b;b=t;}p[b]=a;sz[a]+=sz[b];return true;}}
```

## Complexity
Time O((V+E) α(V)), space O(V).