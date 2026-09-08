# Cheapest Flights Within K Stops

## Problem
Find the cheapest price from `src` to `dst` using at most `k` stops.

## Intuition
Relax flights level by level, where each level represents one additional flight. Use a copy of the previous distances so one iteration cannot use more than the allowed number of edges.

## Java
```java
public int findCheapestPrice(int n,int[][]f,int src,int dst,int k){
    int INF=1_000_000_000;int[]d=new int[n];Arrays.fill(d,INF);d[src]=0;
    for(int i=0;i<=k;i++){int[]nd=d.clone();for(int[]e:f)if(d[e[0]]<INF)nd[e[1]]=Math.min(nd[e[1]],d[e[0]]+e[2]);d=nd;}
    return d[dst]>=INF?-1:d[dst];
}
```

## Complexity
Time O((k+1)E), space O(V).