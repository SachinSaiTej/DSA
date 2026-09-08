# Intersection of Two Arrays

## Problem
Return the distinct values that appear in both arrays.

## Intuition
Put all values from one array into a `HashSet`. While scanning the other array, values found in the set belong to the intersection. A second set prevents duplicates.

## Java
```java
public int[] intersection(int[] nums1, int[] nums2) {
    Set<Integer> first = new HashSet<>();
    for (int x : nums1) first.add(x);

    Set<Integer> result = new HashSet<>();
    for (int x : nums2) {
        if (first.contains(x)) result.add(x);
    }

    return result.stream().mapToInt(Integer::intValue).toArray();
}
```

## Complexity
Time O(n+m) average, space O(n+m) including the result.