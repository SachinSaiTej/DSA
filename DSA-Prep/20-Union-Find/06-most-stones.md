# Most Stones Removed with Same Row or Column

## Problem
Remove the maximum number of stones so that every removed stone shares a row or column with another stone.

## Intuition
Stones connected through shared rows/columns form components. From each component, only one stone must remain, so answer is total stones minus component count.

## Java
```java
public int removeStones(int[][]s){DSU d=new DSU(s.length);for(int i=0;i<s.length;i++)for(int j=i+1;j<s.length;j++)if(s[i][0]==s[j][0]||s[i][1]==s[j][1])d.union(i,j);Set<Integer>roots=new HashSet<>();for(int i=0;i<s.length;i++)roots.add(d.find(i));return s.length-roots.size();}
static class DSU{int[]p;DSU(int n){p=new int[n];for(int i=0;i<n;i++)p[i]=i;}int find(int x){return p[x]==x?x:(p[x]=find(p[x]));}void union(int a,int b){a=find(a);b=find(b);if(a!=b)p[a]=b;}}
```

## Complexity
Time O(n² α(n)), space O(n).