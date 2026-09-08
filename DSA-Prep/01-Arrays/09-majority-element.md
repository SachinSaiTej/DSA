# Majority Element

## Problem
Find the element that appears more than `n/2` times in an array.

## Intuition
Boyer-Moore voting keeps a candidate and a count. A majority element cannot be cancelled out by all other elements combined.

## Java
```java
public int majorityElement(int[] nums) {
    int candidate = 0, count = 0;
    for (int x : nums) {
        if (count == 0) candidate = x;
        count += (x == candidate) ? 1 : -1;
    }
    return candidate;
}
```

## Complexity
Time O(n), space O(1).

## Interview Point
The algorithm relies on the guarantee that a majority element exists. Without that guarantee, verify the candidate afterward.