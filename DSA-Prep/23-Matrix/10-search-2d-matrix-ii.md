# Search a 2D Matrix II

## Problem
Search a target in a matrix where rows and columns are sorted ascending.

## Intuition
Start at the top-right corner. If the value is too large, move left; if too small, move down. Each move eliminates a row or column.

## Java
```java
public boolean searchMatrix(int[][] m,int target){
    int r=0,c=m[0].length-1;
    while(r<m.length&&c>=0){if(m[r][c]==target)return true;if(m[r][c]>target)c--;else r++;}
    return false;
}
```

## Complexity
Time O(R+C), space O(1).