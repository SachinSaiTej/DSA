# Merge Sorted Array

## Problem
Merge two sorted arrays into the first array, which has enough trailing space for all elements.

## Intuition
Fill from the end. Compare the largest remaining elements of both arrays so nothing already placed is overwritten.

## Java
```java
public void merge(int[] nums1,int m,int[] nums2,int n){
    int i=m-1,j=n-1,k=m+n-1;
    while(j>=0){
        if(i>=0&&nums1[i]>nums2[j])nums1[k--]=nums1[i--];
        else nums1[k--]=nums2[j--];
    }
}
```

## Complexity
Time O(m+n), space O(1).