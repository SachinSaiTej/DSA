# Maximum Number of K-Sum Pairs

## Problem
Find the maximum number of pairs whose elements add up to `k`. Each element can be used at most once.

## Intuition
A frequency map lets us greedily match each number with its complement `k - x`. After matching, decrement the available counts.

## Java
```java
public int maxOperations(int[] nums, int k) {
    Map<Integer, Integer> freq = new HashMap<>();
    int operations = 0;

    for (int x : nums) {
        int need = k - x;
        int count = freq.getOrDefault(need, 0);
        if (count > 0) {
            operations++;
            if (count == 1) freq.remove(need);
            else freq.put(need, count - 1);
        } else {
            freq.put(x, freq.getOrDefault(x, 0) + 1);
        }
    }
    return operations;
}
```

## Complexity
Time O(n) average, space O(n).

## Alternative
Sorting plus two pointers also works in O(n log n) time and O(1) auxiliary space.