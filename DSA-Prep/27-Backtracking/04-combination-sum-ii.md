# Combination Sum II

## Problem
Find unique combinations summing to target. Each candidate can be used at most once.

## Intuition
Sort the array and skip equal values at the same recursion depth to prevent duplicate combinations.

## Java
```java
public List<List<Integer>> combinationSum2(int[]a,int target){Arrays.sort(a);List<List<Integer>>ans=new ArrayList<>();dfs(a,0,target,new ArrayList<>(),ans);return ans;}
void dfs(int[]a,int start,int rem,List<Integer>cur,List<List<Integer>>ans){if(rem==0){ans.add(new ArrayList<>(cur));return;}for(int i=start;i<a.length&&a[i]<=rem;i++){if(i>start&&a[i]==a[i-1])continue;cur.add(a[i]);dfs(a,i+1,rem-a[i],cur,ans);cur.remove(cur.size()-1);}}
```

## Complexity
Exponential worst case; recursion depth O(n).