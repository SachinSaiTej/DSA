# Floyd-Warshall

## Problem
Find shortest paths between every pair of vertices.

## Intuition
Allow vertices one by one as intermediate nodes. For every pair `(i, j)`, check whether going through `k` gives a shorter path:

`d[i][j] = min(d[i][j], d[i][k] + d[k][j])`

## Java
```java
public long[][] floydWarshall(long[][] distance) {
    int n = distance.length;

    for (int k = 0; k < n; k++) {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (distance[i][k] == Long.MAX_VALUE ||
                    distance[k][j] == Long.MAX_VALUE) {
                    continue;
                }

                distance[i][j] = Math.min(
                    distance[i][j],
                    distance[i][k] + distance[k][j]
                );
            }
        }
    }

    return distance;
}
```

## Complexity
Time O(V³), space O(V²).