# Subsets

## Problem
Return all subsets of a set of distinct integers.

## Intuition
At each index there are two choices: include the element or skip it. Backtracking explores both choices.

## Java
```java
public List<List<Integer>> subsets(int[] nums){
    List<List<Integer>> ans=new ArrayList<>();
    backtrack(nums,0,new ArrayList<>(),ans); return ans;
}
void backtrack(int[]a,int i,List<Integer>cur,List<List<Integer>>ans){
    if(i==a.length){ans.add(new ArrayList<>(cur));return;}
    backtrack(a,i+1,cur,ans);
    cur.add(a[i]); backtrack(a,i+1,cur,ans); cur.remove(cur.size()-1);
}
```

## Complexity
Time O(n·2^n), space O(n) recursion excluding output.