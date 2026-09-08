# Flood Fill

## Problem
Starting from a cell, recolor the entire connected region having the starting cell's original color.

## Intuition
DFS/BFS visits every adjacent cell with the same original color and changes it to the new color.

## Java
```java
public int[][] floodFill(int[][] image,int sr,int sc,int color){
    int old=image[sr][sc]; if(old==color)return image; dfs(image,sr,sc,old,color); return image;
}
void dfs(int[][] a,int r,int c,int old,int color){
    if(r<0||c<0||r==a.length||c==a[0].length||a[r][c]!=old)return;
    a[r][c]=color; dfs(a,r+1,c,old,color);dfs(a,r-1,c,old,color);dfs(a,r,c+1,old,color);dfs(a,r,c-1,old,color);
}
```

## Complexity
Time O(RC), space O(RC) worst case.