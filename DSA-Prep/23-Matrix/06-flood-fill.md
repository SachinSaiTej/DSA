# Flood Fill

## Problem
Starting from a cell, recolor all 4-directionally connected cells having the same original color.

## Intuition
This is graph traversal on a grid. DFS from the starting cell and recolor each reachable cell so it cannot be visited again.

## Java
```java
public int[][] floodFill(int[][] image,int sr,int sc,int color){
    int old=image[sr][sc]; if(old==color)return image;
    dfs(image,sr,sc,old,color); return image;
}
private void dfs(int[][]a,int r,int c,int old,int color){
    if(r<0||c<0||r==a.length||c==a[0].length||a[r][c]!=old)return;
    a[r][c]=color;
    dfs(a,r+1,c,old,color);dfs(a,r-1,c,old,color);dfs(a,r,c+1,old,color);dfs(a,r,c-1,old,color);
}
```

## Complexity
Time O(RC), space O(RC) worst case.