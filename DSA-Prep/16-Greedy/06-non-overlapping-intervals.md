# Non-overlapping Intervals

## Problem
Find the minimum number of intervals that must be removed so the remaining intervals do not overlap.

## Intuition
Sort by ending time. Keep the interval that finishes earliest because it leaves the most room for the intervals that follow.

## Java
```java
public int eraseOverlapIntervals(int[][] intervals) {
    Arrays.sort(intervals, (a, b) -> Integer.compare(a[1], b[1]));
    int keep = 0;
    int end = Integer.MIN_VALUE;
    for (int[] interval : intervals) {
        if (interval[0] >= end) {
            keep++;
            end = interval[1];
        }
    }
    return intervals.length - keep;
}
```

## Complexity
Time O(n log n), space O(1) apart from sorting.