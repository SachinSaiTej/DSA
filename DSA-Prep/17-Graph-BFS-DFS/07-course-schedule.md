# Course Schedule

## Problem
Determine whether all courses can be completed given prerequisite pairs.

## Intuition
A prerequisite relationship is a directed edge. All courses are possible exactly when the graph has no cycle. DFS uses three states:

- `0` → unvisited
- `1` → currently visiting
- `2` → completely processed

If DFS reaches a node in state `1`, we found a cycle.

## Java
```java
public boolean canFinish(int numCourses, int[][] prerequisites) {
    List<Integer>[] graph = new ArrayList[numCourses];

    for (int i = 0; i < numCourses; i++) {
        graph[i] = new ArrayList<>();
    }

    for (int[] prerequisite : prerequisites) {
        int course = prerequisite[0];
        int required = prerequisite[1];
        graph[required].add(course);
    }

    int[] state = new int[numCourses];

    for (int course = 0; course < numCourses; course++) {
        if (state[course] == 0 && !dfs(graph, course, state)) {
            return false;
        }
    }

    return true;
}

private boolean dfs(List<Integer>[] graph, int course, int[] state) {
    if (state[course] == 1) {
        return false;
    }

    if (state[course] == 2) {
        return true;
    }

    state[course] = 1;

    for (int next : graph[course]) {
        if (!dfs(graph, next, state)) {
            return false;
        }
    }

    state[course] = 2;
    return true;
}
```

## Complexity
Time O(V + E), space O(V + E).