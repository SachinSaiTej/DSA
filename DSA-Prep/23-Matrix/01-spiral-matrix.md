# Spiral Matrix

## Problem
Return all matrix elements in spiral order.

## Intuition
Maintain four boundaries: top, bottom, left, right. Traverse one outer layer at a time and shrink the boundaries.

## Java
```java
public List<Integer> spiralOrder(int[][] m) {
    List<Integer> a=new ArrayList<>();
    if(m.length==0) return a;
    int top=0,bottom=m.length-1,left=0,right=m[0].length-1;
    while(top<=bottom&&left<=right){
        for(int c=left;c<=right;c++) a.add(m[top][c]); top++;
        for(int r=top;r<=bottom;r++) a.add(m[r][right]); right--;
        if(top<=bottom){for(int c=right;c>=left;c--) a.add(m[bottom][c]); bottom--;}
        if(left<=right){for(int r=bottom;r>=top;r--) a.add(m[r][left]); left++;}
    }
    return a;
}
```

## Complexity
Time O(mn), space O(1) excluding output.