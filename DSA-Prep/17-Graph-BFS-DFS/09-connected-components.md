# Number of Connected Components

## Problem
Count connected components in an undirected graph.

## Intuition
Each unvisited node starts one component. DFS marks every node reachable from it.

## Java
```java
public int countComponents(int n,int[][] edges){
    List<Integer>[]g=new ArrayList[n];for(int i=0;i<n;i++)g[i]=new ArrayList<>();
    for(int[]e:edges){g[e[0]].add(e[1]);g[e[1]].add(e[0]);}
    boolean[]v=new boolean[n];int ans=0;for(int i=0;i<n;i++)if(!v[i]){ans++;dfs(g,i,v);}return ans;
}
void dfs(List<Integer>[]g,int u,boolean[]v){v[u]=true;for(int x:g[u])if(!v[x])dfs(g,x,v);}
```

## Complexity
Time O(V+E), space O(V+E).