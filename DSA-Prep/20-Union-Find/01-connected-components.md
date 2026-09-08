# Number of Connected Components

## Problem
Count connected components in an undirected graph.

## Intuition
Union the endpoints of every edge. Each successful union reduces the number of components by one.

## Java
```java
public int countComponents(int n, int[][] edges) {
    DSU dsu = new DSU(n);
    int components = n;

    for (int[] edge : edges) {
        if (dsu.union(edge[0], edge[1])) {
            components--;
        }
    }

    return components;
}

static class DSU {
    int[] parent;
    int[] size;

    DSU(int n) {
        parent = new int[n];
        size = new int[n];

        for (int i = 0; i < n; i++) {
            parent[i] = i;
            size[i] = 1;
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

        if (size[a] < size[b]) {
            int temp = a;
            a = b;
            b = temp;
        }

        parent[b] = a;
        size[a] += size[b];
        return true;
    }
}
```

## Complexity
Time O((V + E) α(V)), space O(V).