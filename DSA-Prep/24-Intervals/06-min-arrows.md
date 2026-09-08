# Minimum Number of Arrows to Burst Balloons

## Problem
Find the minimum arrows needed to burst all balloons represented by x-intervals.

## Intuition
Sort by ending coordinate. Shoot an arrow at the current earliest end; every balloon starting at or before that point is burst.

## Java
```java
public int findMinArrowShots(int[][] a){
    if(a.length==0)return 0;Arrays.sort(a,(x,y)->Integer.compare(x[1],y[1]));
    int arrows=1,end=a[0][1];
    for(int i=1;i<a.length;i++)if(a[i][0]>end){arrows++;end=a[i][1];}
    return arrows;
}
```

## Complexity
Time O(n log n), space O(1) apart from sorting.