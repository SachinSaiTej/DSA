# Subsets

## Intuition
For every element, recursively choose to exclude it or include it. When all elements are processed, record the current subset.

## Java
```java
List<List<Integer>> subsets(int[]a){List<List<Integer>>ans=new ArrayList<>();dfs(a,0,new ArrayList<>(),ans);return ans;}void dfs(int[]a,int i,List<Integer>cur,List<List<Integer>>ans){if(i==a.length){ans.add(new ArrayList<>(cur));return;}dfs(a,i+1,cur,ans);cur.add(a[i]);dfs(a,i+1,cur,ans);cur.remove(cur.size()-1);}
```

## Complexity
O(n·2^n) time and O(n) recursion space excluding output.