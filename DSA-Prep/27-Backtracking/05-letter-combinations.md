# Letter Combinations of a Phone Number

## Problem
Return all possible letter combinations represented by a digit string on a phone keypad.

## Intuition
Each digit gives a set of letters. Backtracking chooses one letter for each digit and explores all combinations.

## Java
```java
public List<String> letterCombinations(String digits){List<String>ans=new ArrayList<>();if(digits.isEmpty())return ans;String[]map={"","","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};dfs(digits,0,new StringBuilder(),ans,map);return ans;}
void dfs(String d,int i,StringBuilder cur,List<String>ans,String[]map){if(i==d.length()){ans.add(cur.toString());return;}for(char ch:map[d.charAt(i)-'0'].toCharArray()){cur.append(ch);dfs(d,i+1,cur,ans,map);cur.deleteCharAt(cur.length()-1);}}
```

## Complexity
Time O(4^n · n), space O(n) excluding output.