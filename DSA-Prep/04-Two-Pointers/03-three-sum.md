# 3Sum

## Problem
Find all unique triplets in an integer array whose sum is zero.

## Intuition
Sort the array. Fix one number, then use two pointers for the remaining two numbers. Skip duplicates to avoid duplicate triplets.

## Java
```java
public List<List<Integer>> threeSum(int[] nums) {
    Arrays.sort(nums);
    List<List<Integer>> ans=new ArrayList<>();
    for(int i=0;i<nums.length-2;i++){
        if(i>0&&nums[i]==nums[i-1]) continue;
        int l=i+1,r=nums.length-1;
        while(l<r){
            long sum=(long)nums[i]+nums[l]+nums[r];
            if(sum==0){ans.add(Arrays.asList(nums[i],nums[l],nums[r]));l++;r--;while(l<r&&nums[l]==nums[l-1])l++;while(l<r&&nums[r]==nums[r+1])r--;}
            else if(sum<0)l++;else r--;
        }
    }
    return ans;
}
```

## Complexity
Time O(n²), space O(1) excluding output.