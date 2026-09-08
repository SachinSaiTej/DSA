# Remove Duplicates from Sorted Array

## Problem
Remove duplicates in-place from a sorted array so each value appears once, returning the new length.

## Intuition
Use a slow pointer for the position of the next unique value and a fast pointer to scan the array.

## Java
```java
public int removeDuplicates(int[] nums){
    if(nums.length==0)return 0;
    int k=1;
    for(int i=1;i<nums.length;i++) if(nums[i]!=nums[i-1]) nums[k++]=nums[i];
    return k;
}
```

## Complexity
Time O(n), space O(1).