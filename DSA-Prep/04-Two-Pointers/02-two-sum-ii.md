# Two Sum II

## Problem
Given a sorted array, find two numbers whose sum equals the target.

## Intuition
Start with the smallest and largest values. If the sum is too small, increase the left pointer; if too large, decrease the right pointer.

## Java
```java
public int[] twoSum(int[] numbers, int target) {
    int l=0,r=numbers.length-1;
    while(l<r){
        int sum=numbers[l]+numbers[r];
        if(sum==target) return new int[]{l+1,r+1};
        if(sum<target) l++; else r--;
    }
    return new int[0];
}
```

## Complexity
Time O(n), space O(1).