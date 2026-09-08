# Sliding Window Maximum

## Problem
Given an array and window size `k`, return the maximum value in every contiguous window.

## Intuition
Maintain a deque of indices whose values are in decreasing order. The front is always the maximum for the current window, while smaller values behind a new larger value can never become maximum.

## Java
```java
public int[] maxSlidingWindow(int[] nums, int k) {
    if (nums.length == 0) return new int[0];
    int[] ans = new int[nums.length - k + 1];
    Deque<Integer> dq = new ArrayDeque<>();
    int out = 0;

    for (int i = 0; i < nums.length; i++) {
        while (!dq.isEmpty() && dq.peekFirst() <= i - k) dq.pollFirst();
        while (!dq.isEmpty() && nums[dq.peekLast()] <= nums[i]) dq.pollLast();
        dq.offerLast(i);
        if (i >= k - 1) ans[out++] = nums[dq.peekFirst()];
    }
    return ans;
}
```

## Complexity
Time O(n), space O(k).