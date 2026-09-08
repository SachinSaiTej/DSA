# Permutations

## Problem
Return all permutations of an array of distinct integers.

## Intuition
Choose one unused number for each position. Once a choice is made, recurse for the next position and undo the choice afterward.

## Java
```java
public List<List<Integer>> permute(int[] nums){
    List<List<Integer>> ans=new ArrayList<>(); boolean[] used=new boolean[nums.length];
    dfs(nums,used,new ArrayList<>(),ans); return ans;
}
void dfs(int[]a,boolean[]u,List<Integer>cur,List<List<Integer>>ans){
    if(cur.size()==a.length){ans.add(new ArrayList<>(cur));return;}
    for(int i=0;i<a.length;i++) if(!u[i]){u[i]=true;cur.add(a[i]);dfs(a,u,cur,ans);cur.remove(cur.size()-1);u[i]=false;}
}
```

## Complexity
Time O(n·n!), space O(n) excluding output.