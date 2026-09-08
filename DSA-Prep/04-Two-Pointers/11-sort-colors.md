# Sort Colors

## Problem
Sort an array containing only `0`, `1`, and `2` in-place.

## Intuition
Use the Dutch National Flag algorithm with three regions: zeroes, ones, and twos. `low` marks the next zero, `mid` scans, and `high` marks the next two.

## Java
```java
public void sortColors(int[] nums){
    int low=0,mid=0,high=nums.length-1;
    while(mid<=high){
        if(nums[mid]==0){int t=nums[low];nums[low++]=nums[mid];nums[mid++]=t;}
        else if(nums[mid]==1)mid++;
        else{int t=nums[mid];nums[mid]=nums[high];nums[high--]=t;}
    }
}
```

## Complexity
Time O(n), space O(1).