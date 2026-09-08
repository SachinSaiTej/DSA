# Floyd-Warshall

## Problem
Find shortest paths between every pair of vertices.

## Intuition
Allow vertices one by one as intermediate nodes. `d[i][j] = min(d[i][j], d[i][k] + d[k][j])`.

## Java
```java
public long[][] floydWarshall(long[][]d){
    int n=d.length;for(int k=0;k<n;k++)for(int i=0;i<n;i++)for(int j=0;j<n;j++)if(d[i][k]!=Long.MAX_VALUE&&d[k][j]!=Long.MAX_VALUE)d[i][j]=Math.min(d[i][j],d[i][k]+d[k][j]);return d;
}
```

## Complexity
Time O(V³), space O(V²).