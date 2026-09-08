# Number of Connected Components

## Problem
Count connected components in an undirected graph.

## Intuition
Each unvisited node starts one component. DFS marks every node reachable from it.

## Java
```java
public int countComponents(int n, int[][] edges) {
    List<Integer>[] graph = new ArrayList[n];

    for (int i = 0; i < n; i++) {
        graph[i] = new ArrayList<>();
    }

    for (int[] edge : edges) {
        graph[edge[0]].add(edge[1]);
        graph[edge[1]].add(edge[0]);
    }

    boolean[] visited = new boolean[n];
    int components = 0;

    for (int node = 0; node < n; node++) {
        if (!visited[node]) {
            components++;
            dfs(graph, node, visited);
        }
    }

    return components;
}

private void dfs(List<Integer>[] graph, int node, boolean[] visited) {
    visited[node] = true;

    for (int neighbor : graph[node]) {
        if (!visited[neighbor]) {
            dfs(graph, neighbor, visited);
        }
    }
}
```

## Complexity
Time O(V + E), space O(V + E).