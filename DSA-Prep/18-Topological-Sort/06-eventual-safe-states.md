# Find Eventual Safe States

## Problem
Return all nodes in a directed graph that eventually reach a terminal node rather than a cycle.

## Intuition
A node is safe if all outgoing neighbors are safe. Reverse the graph and start BFS from terminal nodes (outdegree zero).

## Java
```java
public List<Integer> eventualSafeNodes(int[][]g){
    int n=g.length;List<Integer>[]rev=new ArrayList[n];int[]out=new int[n];for(int i=0;i<n;i++)rev[i]=new ArrayList<>();
    for(int u=0;u<n;u++){out[u]=g[u].length;for(int v:g[u])rev[v].add(u);}
    Queue<Integer>q=new ArrayDeque<>();for(int i=0;i<n;i++)if(out[i]==0)q.offer(i);boolean[]safe=new boolean[n];
    while(!q.isEmpty()){int u=q.poll();safe[u]=true;for(int p:rev[u])if(--out[p]==0)q.offer(p);}List<Integer>a=new ArrayList<>();for(int i=0;i<n;i++)if(safe[i])a.add(i);return a;
}
```

## Complexity
Time O(V+E), space O(V+E).