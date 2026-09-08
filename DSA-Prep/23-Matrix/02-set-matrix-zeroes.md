# Set Matrix Zeroes

## Problem
If an element is zero, set its entire row and column to zero, in place.

## Intuition
Use the first row and first column as marker storage. Track separately whether the original first row/column contained a zero.

## Java
```java
public void setZeroes(int[][] m) {
    int rows=m.length, cols=m[0].length; boolean firstCol=false, firstRow=false;
    for(int c=0;c<cols;c++) if(m[0][c]==0) firstRow=true;
    for(int r=0;r<rows;r++) if(m[r][0]==0) firstCol=true;
    for(int r=1;r<rows;r++) for(int c=1;c<cols;c++) if(m[r][c]==0){m[r][0]=0;m[0][c]=0;}
    for(int r=1;r<rows;r++) for(int c=1;c<cols;c++) if(m[r][0]==0||m[0][c]==0)m[r][c]=0;
    if(firstRow) Arrays.fill(m[0],0);
    if(firstCol) for(int r=0;r<rows;r++) m[r][0]=0;
}
```

## Complexity
Time O(mn), space O(1).