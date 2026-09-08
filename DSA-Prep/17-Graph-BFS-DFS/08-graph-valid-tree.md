# Graph Valid Tree

## Problem
Determine whether `n` nodes and the given undirected edges form one connected acyclic tree.

## Intuition
A tree has exactly `n - 1` edges. Then use DFS to ensure every node is reachable and no edge points back to a visited node other than its parent.

## Java
```java
public boolean validTree(int n, int[][] edges) {
    if (edges.length != n - 1) {
        return false;
    }

    List<Integer>[] graph = new ArrayList[n];
    for (int i = 0; i < n; i++) {
        graph[i] = new ArrayList<>();
    }

    for (int[] edge : edges) {
        graph[edge[0]].add(edge[1]);
        graph[edge[1]].add(edge[0]);
    }

    boolean[] visited = new boolean[n];

    if (!dfs(graph, 0, -1, visited)) {
        return false;
    }

    for (boolean nodeVisited : visited) {
        if (!nodeVisited) {
            return false;
        }
    }

    return true;
}

private boolean dfs(List<Integer>[] graph, int node, int parent, boolean[] visited) {
    visited[node] = true;

    for (int neighbor : graph[node]) {
        if (neighbor == parent) {
            continue;
        }

        if (visited[neighbor] || !dfs(graph, neighbor, node, visited)) {
            return false;
        }
    }

    return true;
}
```

## Complexity
Time O(V + E), space O(V + E).