# Number of Islands

## Problem
Count connected groups of land (`1`) in a grid of land and water (`0`).

## Intuition
Every unvisited land cell starts one island. Run DFS/BFS from it and mark the entire connected component visited.

## Java
```java
public int numIslands(char[][] grid) {
    int count = 0;
    for (int r = 0; r < grid.length; r++)
        for (int c = 0; c < grid[0].length; c++)
            if (grid[r][c] == '1') { count++; dfs(grid, r, c); }
    return count;
}
private void dfs(char[][] g, int r, int c) {
    if (r < 0 || c < 0 || r == g.length || c == g[0].length || g[r][c] != '1') return;
    g[r][c] = '0';
    dfs(g,r+1,c); dfs(g,r-1,c); dfs(g,r,c+1); dfs(g,r,c-1);
}
```

## Complexity
Time O(rows × cols), space O(rows × cols) worst-case recursion.