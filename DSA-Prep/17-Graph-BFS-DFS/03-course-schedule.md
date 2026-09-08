# Course Schedule

## Problem
Given prerequisite pairs, determine whether all courses can be completed.

## Intuition
A valid schedule exists exactly when the directed graph has no cycle. Kahn's BFS removes zero-indegree nodes and detects cycles.

## Java
```java
public boolean canFinish(int n, int[][] prerequisites) {
    List<Integer>[] g = new ArrayList[n];
    for (int i=0;i<n;i++) g[i]=new ArrayList<>();
    int[] indegree = new int[n];
    for (int[] p: prerequisites) { g[p[1]].add(p[0]); indegree[p[0]]++; }
    Queue<Integer> q = new ArrayDeque<>();
    for (int i=0;i<n;i++) if (indegree[i]==0) q.offer(i);
    int done=0;
    while(!q.isEmpty()) {
        int u=q.poll(); done++;
        for(int v:g[u]) if(--indegree[v]==0) q.offer(v);
    }
    return done==n;
}
```

## Complexity
Time O(V + E), space O(V + E).