# Search a 2D Matrix

## Problem
Search a target in a matrix where each row is sorted and each row's first value is greater than the previous row's last value.

## Intuition
Treat the matrix as one sorted 1D array. Binary search index `mid` maps to `row = mid / cols`, `col = mid % cols`.

## Java
```java
public boolean searchMatrix(int[][] m,int target){
    int R=m.length,C=m[0].length,l=0,r=R*C-1;
    while(l<=r){int mid=l+(r-l)/2;int x=m[mid/C][mid%C];if(x==target)return true;if(x<target)l=mid+1;else r=mid-1;}
    return false;
}
```

## Complexity
Time O(log(RC)), space O(1).