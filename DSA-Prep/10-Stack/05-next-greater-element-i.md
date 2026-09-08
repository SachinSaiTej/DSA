# Next Greater Element I

## Problem
For each value in `nums1`, find the first greater value to its right in `nums2`.

## Intuition
Scan `nums2` with a decreasing monotonic stack. When a larger value appears, it becomes the next greater element for all smaller stack values. Store answers in a map.

## Java
```java
public int[] nextGreaterElement(int[] nums1, int[] nums2) {
    Map<Integer, Integer> map = new HashMap<>();
    Deque<Integer> stack = new ArrayDeque<>();
    for (int x : nums2) {
        while (!stack.isEmpty() && x > stack.peek()) map.put(stack.pop(), x);
        stack.push(x);
    }
    while (!stack.isEmpty()) map.putIfAbsent(stack.pop(), -1);
    int[] ans = new int[nums1.length];
    for (int i = 0; i < nums1.length; i++) ans[i] = map.get(nums1[i]);
    return ans;
}
```

## Complexity
Time O(n + m), space O(m).