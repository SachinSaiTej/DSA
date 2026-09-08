# Course Schedule

## Problem
Determine whether all courses can be completed when prerequisites form a directed graph.

## Intuition
Use Kahn's algorithm. Repeatedly take courses with indegree zero. If all courses are removed, there is no cycle.

## Java
```java
public boolean canFinish(int n,int[][] p){
    List<Integer>[]g=new ArrayList[n];for(int i=0;i<n;i++)g[i]=new ArrayList<>();int[]in=new int[n];
    for(int[]e:p){g[e[1]].add(e[0]);in[e[0]]++;}Queue<Integer>q=new ArrayDeque<>();for(int i=0;i<n;i++)if(in[i]==0)q.offer(i);
    int done=0;while(!q.isEmpty()){int u=q.poll();done++;for(int v:g[u])if(--in[v]==0)q.offer(v);}return done==n;
}
```

## Complexity
Time O(V+E), space O(V+E).