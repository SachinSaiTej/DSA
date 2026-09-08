# Graph Valid Tree

## Problem
Determine whether an undirected graph forms a valid tree.

## Intuition
A tree has `n-1` edges and no cycle. Use DSU to reject an edge joining vertices already in the same set.

## Java
```java
public boolean validTree(int n,int[][]e){if(e.length!=n-1)return false;DSU d=new DSU(n);for(int[]x:e)if(!d.union(x[0],x[1]))return false;return true;}
static class DSU{int[]p;DSU(int n){p=new int[n];for(int i=0;i<n;i++)p[i]=i;}int find(int x){return p[x]==x?x:(p[x]=find(p[x]));}boolean union(int a,int b){a=find(a);b=find(b);if(a==b)return false;p[a]=b;return true;}}
```

## Complexity
Time O(E α(V)), space O(V).