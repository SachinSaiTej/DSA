# Generate Parentheses

## Problem
Generate all valid combinations of `n` pairs of parentheses.

## Intuition
At any point, add `(` while fewer than `n` opens are used. Add `)` only when closes are fewer than opens.

## Java
```java
List<String> generateParenthesis(int n){List<String>a=new ArrayList<>();go(n,0,0,new StringBuilder(),a);return a;}void go(int n,int o,int c,StringBuilder s,List<String>a){if(s.length()==2*n){a.add(s.toString());return;}if(o<n){s.append('(');go(n,o+1,c,s,a);s.deleteCharAt(s.length()-1);}if(c<o){s.append(')');go(n,o,c+1,s,a);s.deleteCharAt(s.length()-1);}}
```

## Complexity
O(Cn) output time, where `Cn` is the nth Catalan number; O(n) recursion space excluding output.