# Decode Ways

## Problem
Count ways to decode a digit string where `1..26` map to letters.

## Intuition
At each position, decode one digit if valid or two digits if they form `10..26`. Keep the previous two DP values.

## Java
```java
public int numDecodings(String s){if(s.isEmpty()||s.charAt(0)=='0')return 0;int p2=1,p1=1;for(int i=1;i<s.length();i++){int cur=0;if(s.charAt(i)!='0')cur+=p1;int two=Integer.parseInt(s.substring(i-1,i+1));if(two>=10&&two<=26)cur+=p2;p2=p1;p1=cur;}return p1;}
```

## Complexity
Time O(n), space O(1).