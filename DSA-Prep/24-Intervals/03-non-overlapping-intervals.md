# Non-overlapping Intervals

## Problem
Find the minimum number of intervals to remove so the remaining intervals do not overlap.

## Intuition
Sort by end time. Always keep the interval that finishes earliest because it leaves the most room for future intervals.

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