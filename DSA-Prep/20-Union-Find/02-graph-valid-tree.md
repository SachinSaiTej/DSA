# Graph Valid Tree

## Problem
Determine whether an undirected graph forms a valid tree.

## Intuition
A tree has `n - 1` edges and no cycle. Use DSU to reject an edge joining vertices already in the same set.

## Java
```java
public boolean validTree(int n, int[][] edges) {
    if (edges.length != n - 1) {
        return false;
    }

    DSU dsu = new DSU(n);

    for (int[] edge : edges) {
        if (!dsu.union(edge[0], edge[1])) {
            return false;
        }
    }

    return true;
}

static class DSU {
    int[] parent;

    DSU(int n) {
        parent = new int[n];

        for (int i = 0; i < n; i++) {
            parent[i] = i;
        }
    }

    int find(int x) {
        if (parent[x] == x) {
            return x;
        }

        parent[x] = find(parent[x]);
        return parent[x];
    }

    boolean union(int a, int b) {
        a = find(a);
        b = find(b);

        if (a == b) {
            return false;
        }

        parent[a] = b;
        return true;
    }
}
```

## Complexity
Time O(E α(V)), space O(V).