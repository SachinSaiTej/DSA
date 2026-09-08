# Minimum Number of Arrows

## Intuition
Sort balloons by ending coordinate. Shoot an arrow at the earliest ending point. Every overlapping balloon is burst by that arrow; when a balloon starts after the current point, a new arrow is required.

## Java
```java
public int findMinArrowShots(int[][]p){if(p.length==0)return 0;Arrays.sort(p,(a,b)->Integer.compare(a[1],b[1]));int arrows=1,end=p[0][1];for(int i=1;i<p.length;i++)if(p[i][0]>end){arrows++;end=p[i][1];}return arrows;}
```

## Complexity
O(n log n) time and O(1) extra space apart from sorting.