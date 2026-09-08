# Bellman-Ford

## Problem
Find shortest paths from a source even when negative edge weights are present, and detect negative cycles reachable from the source.

## Intuition
Relax every edge `V-1` times. A further improvement means a negative cycle exists.

## Java
```java
public int[] bellmanFord(int n,int[][]edges,int src){
    int[]d=new int[n];Arrays.fill(d,Integer.MAX_VALUE);d[src]=0;
    for(int i=1;i<n;i++){boolean changed=false;for(int[]e:edges)if(d[e[0]]!=Integer.MAX_VALUE&&d[e[1]]>d[e[0]]+e[2]){d[e[1]]=d[e[0]]+e[2];changed=true;}if(!changed)break;}
    for(int[]e:edges)if(d[e[0]]!=Integer.MAX_VALUE&&d[e[1]]>d[e[0]]+e[2])throw new IllegalArgumentException("Negative cycle");return d;
}
```

## Complexity
Time O(VE), space O(V).