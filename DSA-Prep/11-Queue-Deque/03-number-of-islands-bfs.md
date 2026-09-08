# Number of Islands — BFS

## Problem
Count the number of connected islands of `1`s in a grid, using BFS.

## Intuition
Whenever we find an unvisited land cell, it starts a new island. BFS visits every connected land cell and marks it visited.

## Java
```java
public int numIslands(char[][] grid) {
    int rows = grid.length, cols = grid[0].length, count = 0;
    int[][] dirs = {{1,0},{-1,0},{0,1},{0,-1}};
    Queue<int[]> q = new ArrayDeque<>();

    for (int r = 0; r < rows; r++) {
        for (int c = 0; c < cols; c++) {
            if (grid[r][c] != '1') continue;
            count++;
            grid[r][c] = '0';
            q.offer(new int[]{r,c});
            while (!q.isEmpty()) {
                int[] cur = q.poll();
                for (int[] d : dirs) {
                    int nr = cur[0] + d[0], nc = cur[1] + d[1];
                    if (nr >= 0 && nr < rows && nc >= 0 && nc < cols && grid[nr][nc] == '1') {
                        grid[nr][nc] = '0';
                        q.offer(new int[]{nr,nc});
                    }
                }
            }
        }
    }
    return count;
}
```

## Complexity
Time O(rows × cols), space O(rows × cols) in the worst case.