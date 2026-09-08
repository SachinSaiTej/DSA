# First Unique Character

## Problem
Return the index of the first character that occurs exactly once, or `-1`.

## Intuition
Count frequencies first, then scan the string again in original order and return the first character with frequency one.

## Java
```java
public int firstUniqChar(String s) {
    Map<Character,Integer> freq=new HashMap<>();
    for(char c:s.toCharArray()) freq.merge(c,1,Integer::sum);
    for(int i=0;i<s.length();i++) if(freq.get(s.charAt(i))==1) return i;
    return -1;
}
```

## Complexity
Time O(n), space O(k).