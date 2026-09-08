# Course Schedule

## Problem
Determine whether all courses can be completed given prerequisite pairs.

## Intuition
A prerequisite relationship is a directed edge. All courses are possible exactly when the graph has no cycle. DFS uses three states: unvisited, visiting, visited.

## Java
```java
public boolean canFinish(int n,int[][] p){
    List<Integer>[] g=new ArrayList[n];for(int i=0;i<n;i++)g[i]=new ArrayList<>();
    for(int[] e:p)g[e[1]].add(e[0]); int[] state=new int[n];
    for(int i=0;i<n;i++)if(state[i]==0&&!dfs(g,i,state))return false; return true;
}
boolean dfs(List<Integer>[]g,int u,int[]s){
    if(s[u]==1)return false;if(s[u]==2)return true;s[u]=1;
    for(int v:g[u])if(!dfs(g,v,s))return false;s[u]=2;return true;
}
```

## Complexity
Time O(V+E), space O(V+E).