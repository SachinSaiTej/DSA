# Ransom Note

## Problem
Determine whether a ransom note can be constructed from the characters available in a magazine, using each character at most as many times as it appears.

## Intuition
Count available magazine characters, then consume one count for every character in the note.

## Java
```java
public boolean canConstruct(String ransomNote, String magazine) {
    int[] count=new int[26];
    for(char c:magazine.toCharArray()) count[c-'a']++;
    for(char c:ransomNote.toCharArray()) if(--count[c-'a']<0) return false;
    return true;
}
```

## Complexity
Time O(n + m), space O(1) for lowercase English letters.