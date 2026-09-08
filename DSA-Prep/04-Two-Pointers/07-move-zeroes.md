# Move Zeroes

## Problem
Move all zeroes to the end of the array while preserving the relative order of non-zero elements.

## Intuition
Use a write pointer for the next non-zero position. After placing all non-zero values, fill the remaining positions with zeroes.

## Java
```java
public void moveZeroes(int[] nums){
    int write=0;
    for(int x:nums) if(x!=0) nums[write++]=x;
    while(write<nums.length) nums[write++]=0;
}
```

## Complexity
Time O(n), space O(1).