# Course Schedule II

## Problem
Return an ordering of courses that satisfies all prerequisites, or an empty array if impossible.

## Intuition
Topological ordering is exactly a valid course order. Use indegrees and BFS; a cycle leaves some courses unprocessed.

## Java
```java
public int[] findOrder(int n,int[][]p){
    List<Integer>[]g=new ArrayList[n];for(int i=0;i<n;i++)g[i]=new ArrayList<>();int[]in=new int[n];
    for(int[]e:p){g[e[1]].add(e[0]);in[e[0]]++;}Queue<Integer>q=new ArrayDeque<>();for(int i=0;i<n;i++)if(in[i]==0)q.offer(i);
    int[]ans=new int[n];int k=0;while(!q.isEmpty()){int u=q.poll();ans[k++]=u;for(int v:g[u])if(--in[v]==0)q.offer(v);}return k==n?ans:new int[0];
}
```

## Complexity
Time O(V+E), space O(V+E).