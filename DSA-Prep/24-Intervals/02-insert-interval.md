# Insert Interval

## Problem
Insert a new interval into sorted, non-overlapping intervals and merge overlaps.

## Intuition
Add all intervals ending before the new interval, merge every overlapping interval into it, then append the remaining intervals.

## Java
```java
public int[][] insert(int[][] a,int[] n){
    List<int[]>out=new ArrayList<>();int i=0;
    while(i<a.length&&a[i][1]<n[0])out.add(a[i++]);
    while(i<a.length&&a[i][0]<=n[1]){n[0]=Math.min(n[0],a[i][0]);n[1]=Math.max(n[1],a[i][1]);i++;}
    out.add(n);while(i<a.length)out.add(a[i++]);return out.toArray(new int[0][]);
}
```

## Complexity
Time O(n), space O(n) for output.