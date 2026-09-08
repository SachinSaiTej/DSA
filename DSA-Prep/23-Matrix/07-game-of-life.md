# Game of Life

## Problem
Compute the next state of Conway's Game of Life in-place.

## Intuition
Each cell depends on its eight neighbors. Encode a transition without losing the original state: `-1` means live→dead and `2` means dead→live. Use `abs(value)==1` to read the original state.

## Java
```java
public void gameOfLife(int[][] b){
    int R=b.length,C=b[0].length;
    int[][] d={{-1,-1},{-1,0},{-1,1},{0,-1},{0,1},{1,-1},{1,0},{1,1}};
    for(int r=0;r<R;r++)for(int c=0;c<C;c++){
        int live=0; for(int[]x:d){int nr=r+x[0],nc=c+x[1];if(nr>=0&&nc>=0&&nr<R&&nc<C&&Math.abs(b[nr][nc])==1)live++;}
        if(b[r][c]==1&&(live<2||live>3))b[r][c]=-1;
        else if(b[r][c]==0&&live==3)b[r][c]=2;
    }
    for(int r=0;r<R;r++)for(int c=0;c<C;c++)if(b[r][c]==-1)b[r][c]=0;else if(b[r][c]==2)b[r][c]=1;
}
```

## Complexity
Time O(RC), space O(1).