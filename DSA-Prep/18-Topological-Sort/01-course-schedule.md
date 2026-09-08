# Course Schedule

## Problem
Determine whether all courses can be completed when prerequisites form a directed graph.

## Intuition
Use Kahn's algorithm. Repeatedly take courses with indegree zero. If all courses are removed, there is no cycle.

## Java
```java
public boolean canFinish(int n, int[][] prerequisites) {
    List<Integer>[] graph = new ArrayList[n];
    int[] indegree = new int[n];

    for (int i = 0; i < n; i++) {
        graph[i] = new ArrayList<>();
    }

    for (int[] edge : prerequisites) {
        graph[edge[1]].add(edge[0]);
        indegree[edge[0]]++;
    }

    Queue<Integer> queue = new ArrayDeque<>();

    for (int course = 0; course < n; course++) {
        if (indegree[course] == 0) {
            queue.offer(course);
        }
    }

    int completed = 0;

    while (!queue.isEmpty()) {
        int course = queue.poll();
        completed++;

        for (int next : graph[course]) {
            indegree[next]--;

            if (indegree[next] == 0) {
                queue.offer(next);
            }
        }
    }

    return completed == n;
}
```

## Complexity
Time O(V + E), space O(V + E).