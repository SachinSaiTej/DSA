# Dijkstra's Algorithm

## Problem
Find shortest paths from a source to every vertex in a graph with non-negative edge weights.

## Intuition
Always finalize the unvisited vertex with the smallest tentative distance, then relax its outgoing edges using a min-heap.

## Java
```java
public int[] dijkstra(List<int[]>[]g,int src){
    int n=g.length;int[]d=new int[n];Arrays.fill(d,Integer.MAX_VALUE);d[src]=0;PriorityQueue<int[]>pq=new PriorityQueue<>((a,b)->Integer.compare(a[1],b[1]));pq.offer(new int[]{src,0});
    while(!pq.isEmpty()){int[]x=pq.poll();int u=x[0];if(x[1]!=d[u])continue;for(int[]e:g[u])if(d[e[0]]>d[u]+e[1]){d[e[0]]=d[u]+e[1];pq.offer(new int[]{e[0],d[e[0]]});}}return d;
}
```

## Complexity
Time O((V+E) log V), space O(V+E).