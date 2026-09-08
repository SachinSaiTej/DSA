# Combination Sum

## Problem
Find all unique combinations of candidates that sum to target. A candidate may be reused.

## Intuition
At each candidate, either take it again or move to the next candidate. Stop when the remaining target becomes zero or negative.

## Java
```java
public List<List<Integer>> combinationSum(int[]a,int target){Arrays.sort(a);List<List<Integer>>ans=new ArrayList<>();dfs(a,0,target,new ArrayList<>(),ans);return ans;}
void dfs(int[]a,int start,int rem,List<Integer>cur,List<List<Integer>>ans){if(rem==0){ans.add(new ArrayList<>(cur));return;}for(int i=start;i<a.length&&a[i]<=rem;i++){cur.add(a[i]);dfs(a,i,rem-a[i],cur,ans);cur.remove(cur.size()-1);}}
```

## Complexity
Exponential in the worst case; space O(target) recursion depth.