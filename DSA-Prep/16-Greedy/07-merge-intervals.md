# Merge Intervals

## Problem
Merge all overlapping intervals and return the non-overlapping intervals covering the same ranges.

## Intuition
Sort intervals by start time. Compare each interval with the last merged interval. If they overlap, extend its end; otherwise add a new interval.

## Java
```java
public int[][] merge(int[][] intervals) {
    Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
    List<int[]> ans = new ArrayList<>();
    for (int[] cur : intervals) {
        if (ans.isEmpty() || ans.get(ans.size() - 1)[1] < cur[0]) {
            ans.add(new int[]{cur[0], cur[1]});
        } else {
            int[] last = ans.get(ans.size() - 1);
            last[1] = Math.max(last[1], cur[1]);
        }
    }
    return ans.toArray(new int[0][]);
}
```

## Complexity
Time O(n log n), space O(n) for the output.