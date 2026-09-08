# Rotting Oranges

## Problem
Find the minimum minutes until all reachable fresh oranges become rotten; return -1 if impossible.

## Intuition
Multi-source BFS starts from every rotten orange simultaneously. Each BFS level represents one minute.

## Java
```java
public int orangesRotting(int[][] grid) {
    Queue<int[]> q = new ArrayDeque<>();
    int fresh=0;
    for(int r=0;r<grid.length;r++) for(int c=0;c<grid[0].length;c++) {
        if(grid[r][c]==2) q.offer(new int[]{r,c});
        if(grid[r][c]==1) fresh++;
    }
    int minutes=0;
    int[][] d={{1,0},{-1,0},{0,1},{0,-1}};
    while(!q.isEmpty() && fresh>0) {
        for(int sz=q.size();sz>0;sz--) {
            int[] p=q.poll();
            for(int[] x:d){int nr=p[0]+x[0],nc=p[1]+x[1];
                if(nr>=0&&nc>=0&&nr<grid.length&&nc<grid[0].length&&grid[nr][nc]==1){grid[nr][nc]=2;fresh--;q.offer(new int[]{nr,nc});}
            }
        }
        minutes++;
    }
    return fresh==0?minutes:-1;
}
```

## Complexity
Time O(RC), space O(RC).