# Intersection of Two Arrays

## Problem
Return the distinct values that appear in both arrays.

## Intuition
Put the first array into a set, then scan the second array. A second set prevents duplicates in the result.

## Java
```java
public int[] intersection(int[] nums1, int[] nums2) {
    Set<Integer> set = new HashSet<>();
    for (int x : nums1) set.add(x);
    Set<Integer> common = new HashSet<>();
    for (int x : nums2) if (set.contains(x)) common.add(x);
    return common.stream().mapToInt(Integer::intValue).toArray();
}
```

## Complexity
Time O(n + m) average, space O(n + m) including output.