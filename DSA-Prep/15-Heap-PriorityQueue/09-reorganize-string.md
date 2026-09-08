# Reorganize String

## Problem
Rearrange characters so no two adjacent characters are equal, or return an empty string if impossible.

## Intuition
Always place the most frequent remaining character, while keeping the previously used character unavailable for the next position.

## Java
```java
public String reorganizeString(String s){int[]f=new int[26];for(char c:s.toCharArray())f[c-'a']++;PriorityQueue<int[]>q=new PriorityQueue<>((a,b)->b[1]-a[1]);for(int i=0;i<26;i++)if(f[i]>0)q.offer(new int[]{i,f[i]});StringBuilder out=new StringBuilder();int[]prev=null;while(!q.isEmpty()){int[]cur=q.poll();out.append((char)('a'+cur[0]));cur[1]--;if(prev!=null&&prev[1]>0)q.offer(prev);prev=cur;}return out.length()==s.length()?out.toString():"";}
```

## Complexity
O(n log 26) time and O(26) space.