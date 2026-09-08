# Interval List Intersections

## Problem
Find intersections between two sorted lists of disjoint intervals.

## Intuition
For two current intervals, their intersection is `[max(starts), min(ends)]` if start <= end. Move the interval that ends first.

## Java
```java
public int[][] intervalIntersection(int[][] a,int[][] b){
    List<int[]>out=new ArrayList<>();int i=0,j=0;
    while(i<a.length&&j<b.length){int s=Math.max(a[i][0],b[j][0]),e=Math.min(a[i][1],b[j][1]);if(s<=e)out.add(new int[]{s,e});if(a[i][1]<b[j][1])i++;else j++;}
    return out.toArray(new int[0][]);
}
```

## Complexity
Time O(m+n), space O(m+n) for output.