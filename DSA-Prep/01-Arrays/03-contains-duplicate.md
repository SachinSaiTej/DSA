# Contains Duplicate

## Problem
Determine whether an integer array contains any value more than once.

## Intuition
A `HashSet` stores values already seen. If a value is already present, we have found a duplicate.

## Java
```java
public boolean containsDuplicate(int[] nums) {
    Set<Integer> seen = new HashSet<>();
    for (int x : nums) {
        if (!seen.add(x)) return true;
    }
    return false;
}
```

## Complexity
Time O(n) average, space O(n).

## Alternative
Sorting first also works in O(n log n) time and O(1) auxiliary space depending on the sorting implementation.