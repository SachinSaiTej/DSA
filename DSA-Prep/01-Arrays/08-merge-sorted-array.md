# Merge Sorted Array

## Problem
Merge two sorted arrays into `nums1`, where `nums1` has enough space for all elements.

## Intuition
Merge from the end. The largest remaining value belongs at the largest free position, so we avoid overwriting useful values in `nums1`.

## Java
```java
public void merge(int[] nums1, int m, int[] nums2, int n) {
    int i = m - 1, j = n - 1, k = m + n - 1;
    while (j >= 0) {
        if (i >= 0 && nums1[i] > nums2[j]) nums1[k--] = nums1[i--];
        else nums1[k--] = nums2[j--];
    }
}
```

## Complexity
Time O(m+n), space O(1).