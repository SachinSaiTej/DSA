# Non-overlapping Intervals

## Problem
Find the minimum number of intervals to remove so the remaining intervals do not overlap.

## Intuition
Sort by end time. Keep the interval that finishes earliest; it leaves the most room for future intervals.

## Java
```java
public int eraseOverlapIntervals(int[][] a) {
    Arrays.sort(a,(x,y)->Integer.compare(x[1],y[1]));
    int keep=0,end=Integer.MIN_VALUE;
    for(int[] x:a) if(x[0]>=end){keep++;end=x[1];}
    return a.length-keep;
}
```

## Complexity
Time O(n log n), space O(1) apart from sorting.