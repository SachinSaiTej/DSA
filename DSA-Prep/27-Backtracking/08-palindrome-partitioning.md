# Palindrome Partitioning

## Problem
Partition a string so every substring in the partition is a palindrome.

## Intuition
Choose the next cut at every position, but recurse only when the chosen substring is a palindrome.

## Java
```java
public List<List<String>> partition(String s){List<List<String>>ans=new ArrayList<>();dfs(s,0,new ArrayList<>(),ans);return ans;}
void dfs(String s,int start,List<String>cur,List<List<String>>ans){if(start==s.length()){ans.add(new ArrayList<>(cur));return;}for(int end=start;end<s.length();end++)if(isPal(s,start,end)){cur.add(s.substring(start,end+1));dfs(s,end+1,cur,ans);cur.remove(cur.size()-1);}}
boolean isPal(String s,int l,int r){while(l<r)if(s.charAt(l++)!=s.charAt(r--))return false;return true;}
```

## Complexity
Worst case O(n·2^n) time, O(n) recursion depth excluding output.