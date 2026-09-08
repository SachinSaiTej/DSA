# Restore IP Addresses

## Problem
Return all valid IP addresses formed by inserting three dots into a string of digits.

## Intuition
An IP has exactly four parts. Backtrack over possible part lengths 1–3, rejecting leading zeroes and values greater than 255.

## Java
```java
public List<String> restoreIpAddresses(String s){List<String>ans=new ArrayList<>();dfs(s,0,0,new StringBuilder(),ans);return ans;}
void dfs(String s,int pos,int parts,StringBuilder cur,List<String>a){if(parts==4){if(pos==s.length())a.add(cur.substring(0,cur.length()-1));return;}for(int len=1;len<=3&&pos+len<=s.length();len++){if(len>1&&s.charAt(pos)=='0')break;int v=Integer.parseInt(s.substring(pos,pos+len));if(v>255)break;int old=cur.length();cur.append(v).append('.');dfs(s,pos+len,parts+1,cur,a);cur.setLength(old);}}
```

## Complexity
Constant-bounded branching, with O(n) recursion space excluding output.