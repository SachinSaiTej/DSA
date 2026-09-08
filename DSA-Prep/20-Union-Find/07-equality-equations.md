# Satisfiability of Equality Equations

## Problem
Determine whether equations like `a==b` and `a!=b` can all be true simultaneously.

## Intuition
Union every equality first. Then any inequality whose variables have the same root is a contradiction.

## Java
```java
public boolean equationsPossible(String[]e){DSU d=new DSU(26);for(String s:e)if(s.charAt(1)=='=')d.union(s.charAt(0)-'a',s.charAt(3)-'a');for(String s:e)if(s.charAt(1)=='!'&&d.find(s.charAt(0)-'a')==d.find(s.charAt(3)-'a'))return false;return true;}
static class DSU{int[]p;DSU(int n){p=new int[n];for(int i=0;i<n;i++)p[i]=i;}int find(int x){return p[x]==x?x:(p[x]=find(p[x]));}void union(int a,int b){a=find(a);b=find(b);if(a!=b)p[a]=b;}}
```

## Complexity
Time O(E α(26)), space O(26).