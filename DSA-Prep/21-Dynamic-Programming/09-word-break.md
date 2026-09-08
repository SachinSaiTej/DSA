# Word Break

## Problem
Determine whether a string can be segmented into dictionary words.

## Intuition
`dp[i]` means the prefix ending before `i` can be segmented. Try every dictionary word as the final piece.

## Java
```java
public boolean wordBreak(String s,List<String>words){Set<String>set=new HashSet<>(words);boolean[]dp=new boolean[s.length()+1];dp[0]=true;for(int i=1;i<=s.length();i++)for(int j=0;j<i;j++)if(dp[j]&&set.contains(s.substring(j,i))){dp[i]=true;break;}return dp[s.length()];}
```

## Complexity
Time O(n²) substring checks (Java implementations may add substring costs), space O(n).