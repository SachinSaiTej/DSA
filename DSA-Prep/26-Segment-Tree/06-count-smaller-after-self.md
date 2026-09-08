# Count of Smaller Numbers After Self

## Problem
For every array element, count how many smaller elements appear to its right.

## Intuition
Process values from right to left. Coordinate-compress the values, then use a Fenwick tree to query how many previously seen values are smaller.

## Java
```java
public List<Integer> countSmaller(int[] nums){
    int[]v=nums.clone();Arrays.sort(v);Map<Integer,Integer>rank=new HashMap<>();int k=1;for(int x:v)rank.putIfAbsent(x,k++);
    Fenwick f=new Fenwick(k+1);Integer[]ans=new Integer[nums.length];
    for(int i=nums.length-1;i>=0;i--){int r=rank.get(nums[i]);ans[i]=f.sum(r-1);f.add(r,1);}
    return Arrays.asList(ans);
}
static class Fenwick{int[]b;Fenwick(int n){b=new int[n+1];}void add(int i,int d){for(;i<b.length;i+=i&-i)b[i]+=d;}int sum(int i){int s=0;for(;i>0;i-=i&-i)s+=b[i];return s;}}
```

## Complexity
Time O(n log n), space O(n).