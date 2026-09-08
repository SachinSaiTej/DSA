# Network Delay Time

## Problem
Find how long it takes for a signal from node `k` to reach every node in a directed weighted graph.

## Intuition
This is single-source shortest path with non-negative weights. Dijkstra gives the shortest distance to every node; the answer is the maximum distance.

## Java
```java
public int networkDelayTime(int[][]t,int n,int k){
    List<int[]>[]g=new ArrayList[n+1];for(int i=1;i<=n;i++)g[i]=new ArrayList<>();for(int[]e:t)g[e[0]].add(new int[]{e[1],e[2]});
    int[]d=new int[n+1];Arrays.fill(d,Integer.MAX_VALUE);d[k]=0;PriorityQueue<int[]>pq=new PriorityQueue<>((a,b)->a[1]-b[1]);pq.offer(new int[]{k,0});
    while(!pq.isEmpty()){int[]x=pq.poll();int u=x[0];if(x[1]!=d[u])continue;for(int[]e:g[u])if(d[e[0]]>d[u]+e[1]){d[e[0]]=d[u]+e[1];pq.offer(new int[]{e[0],d[e[0]]});}}
    int ans=0;for(int i=1;i<=n;i++)if(d[i]==Integer.MAX_VALUE)return -1;else ans=Math.max(ans,d[i]);return ans;
}
```

## Complexity
Time O((V+E) log V), space O(V+E).