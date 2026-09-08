# Generate Parentheses

## Problem
Generate all valid strings containing `n` pairs of parentheses.

## Intuition
At any point we can add `(` if fewer than n opens have been used, and add `)` only if it will not exceed the number of opens used.

## Java
```java
public List<String> generateParenthesis(int n){List<String>ans=new ArrayList<>();dfs(n,0,0,new StringBuilder(),ans);return ans;}
void dfs(int n,int open,int close,StringBuilder s,List<String>a){if(s.length()==2*n){a.add(s.toString());return;}if(open<n){s.append('(');dfs(n,open+1,close,s,a);s.deleteCharAt(s.length()-1);}if(close<open){s.append(')');dfs(n,open,close+1,s,a);s.deleteCharAt(s.length()-1);}}
```

## Complexity
O(Cn · n) output-sensitive, where Cn is the nth Catalan number.