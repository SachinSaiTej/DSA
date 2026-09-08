# Graph Valid Tree

## Problem
Determine whether `n` nodes and the given undirected edges form one connected acyclic tree.

## Intuition
A tree has exactly `n-1` edges. Then use DFS to ensure every node is reachable and no edge points back to a visited node other than its parent.

## Java
```java
public boolean validTree(int n,int[][] edges){
    if(edges.length!=n-1)return false; List<Integer>[]g=new ArrayList[n];for(int i=0;i<n;i++)g[i]=new ArrayList<>();
    for(int[]e:edges){g[e[0]].add(e[1]);g[e[1]].add(e[0]);}
    boolean[]v=new boolean[n]; if(!dfs(g,0,-1,v))return false; for(boolean x:v)if(!x)return false; return true;
}
boolean dfs(List<Integer>[]g,int u,int parent,boolean[]v){v[u]=true;for(int x:g[u]){if(x==parent)continue;if(v[x]||!dfs(g,x,u,v))return false;}return true;}
```

## Complexity
Time O(V+E), space O(V+E).