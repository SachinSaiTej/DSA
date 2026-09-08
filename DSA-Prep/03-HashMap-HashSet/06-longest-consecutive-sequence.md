# Longest Consecutive Sequence

## Problem
Find the length of the longest sequence of consecutive integers in an unsorted array.

## Intuition
Put all values in a set. Only start counting from a number whose predecessor is absent. This ensures each sequence is processed once.

## Java
```java
public int longestConsecutive(int[] nums) {
    Set<Integer> set = new HashSet<>();
    for (int x : nums) set.add(x);
    int best = 0;
    for (int x : set) {
        if (!set.contains(x - 1)) {
            int cur = x, len = 1;
            while (set.contains(cur + 1)) { cur++; len++; }
            best = Math.max(best, len);
        }
    }
    return best;
}
```

## Complexity
Time O(n) average, space O(n).