# Rotate Image

## Problem
Rotate an `n x n` matrix 90 degrees clockwise in-place.

## Intuition
Transpose the matrix, then reverse every row. Transpose swaps rows and columns; reversing rows produces the clockwise rotation.

## Java
```java
public void rotate(int[][] m) {
    int n=m.length;
    for(int r=0;r<n;r++) for(int c=r+1;c<n;c++) {
        int t=m[r][c]; m[r][c]=m[c][r]; m[c][r]=t;
    }
    for(int r=0;r<n;r++) for(int l=0,h=n-1;l<h;l++,h--) {
        int t=m[r][l]; m[r][l]=m[r][h]; m[r][h]=t;
    }
}
```

## Complexity
Time O(n²), space O(1).