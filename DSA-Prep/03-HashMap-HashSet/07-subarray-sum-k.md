# Subarray Sum Equals K

## Problem
Count continuous subarrays whose sum equals `k`.

## Intuition
Let `prefix` be the running sum. A previous prefix of `prefix - k` means the elements between those two positions sum to k. Store prefix-sum frequencies in a map.

## Java
```java
public int subarraySum(int[] nums, int k) {
    Map<Integer, Integer> freq = new HashMap<>();
    freq.put(0, 1);
    int prefix = 0, ans = 0;
    for (int x : nums) {
        prefix += x;
        ans += freq.getOrDefault(prefix - k, 0);
        freq.merge(prefix, 1, Integer::sum);
    }
    return ans;
}
```

## Complexity
Time O(n), space O(n).