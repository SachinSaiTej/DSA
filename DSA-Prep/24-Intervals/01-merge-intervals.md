# Merge Intervals

## Problem
Merge all overlapping intervals.

## Intuition
Sort by start time. If the next interval starts before the current interval ends, extend the current end; otherwise start a new interval.

## Java
```java
public int[][] merge(int[][] intervals) {
    Arrays.sort(intervals,(a,b)->Integer.compare(a[0],b[0]));
    List<int[]> out=new ArrayList<>();
    for(int[] cur:intervals){
        if(out.isEmpty()||out.get(out.size()-1)[1]<cur[0]) out.add(cur.clone());
        else out.get(out.size()-1)[1]=Math.max(out.get(out.size()-1)[1],cur[1]);
    }
    return out.toArray(new int[0][]);
}
```

## Complexity
Time O(n log n), space O(n) for output.