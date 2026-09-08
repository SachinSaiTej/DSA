# Contains Duplicate

## Problem
Given an integer array, determine whether any value appears at least twice.

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

## Interview Insight
`HashSet.add()` returning `false` is a clean way to detect a repeated value.