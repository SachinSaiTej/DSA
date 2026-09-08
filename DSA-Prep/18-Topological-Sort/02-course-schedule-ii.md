# Course Schedule II

## Problem
Return an ordering of courses that satisfies all prerequisites, or an empty array if impossible.

## Intuition
Topological ordering is exactly a valid course order. Use indegrees and BFS; a cycle leaves some courses unprocessed.

## Java
```java
public int[] findOrder(int n, int[][] prerequisites) {
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

    int[] order = new int[n];
    int index = 0;

    while (!queue.isEmpty()) {
        int course = queue.poll();
        order[index++] = course;

        for (int next : graph[course]) {
            indegree[next]--;

            if (indegree[next] == 0) {
                queue.offer(next);
            }
        }
    }

    return index == n ? order : new int[0];
}
```

## Complexity
Time O(V + E), space O(V + E).