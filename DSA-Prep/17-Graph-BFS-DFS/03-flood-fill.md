# Flood Fill

## Problem
Starting from a cell, recolor the entire connected region having the starting cell's original color.

## Intuition
DFS/BFS visits every adjacent cell with the same original color and changes it to the new color.

## Java
```java
public int[][] floodFill(int[][] image, int sr, int sc, int color) {
    int oldColor = image[sr][sc];

    if (oldColor == color) {
        return image;
    }

    dfs(image, sr, sc, oldColor, color);
    return image;
}

private void dfs(int[][] image, int row, int col, int oldColor, int newColor) {
    if (row < 0 || col < 0 ||
        row >= image.length || col >= image[0].length ||
        image[row][col] != oldColor) {
        return;
    }

    image[row][col] = newColor;

    dfs(image, row + 1, col, oldColor, newColor);
    dfs(image, row - 1, col, oldColor, newColor);
    dfs(image, row, col + 1, oldColor, newColor);
    dfs(image, row, col - 1, oldColor, newColor);
}
```

## Complexity
Time O(RC), space O(RC) worst case.