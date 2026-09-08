# Valid Anagram

## Problem
Given two strings, determine whether one is an anagram of the other.

## Intuition
Two strings are anagrams when every character appears the same number of times. Count characters from the first string and subtract using the second.

## Java
```java
public boolean isAnagram(String s, String t) {
    if (s.length() != t.length()) return false;
    int[] count = new int[26];
    for (char c : s.toCharArray()) count[c - 'a']++;
    for (char c : t.toCharArray()) {
        if (--count[c - 'a'] < 0) return false;
    }
    return true;
}
```

## Complexity
Time O(n), space O(1) for lowercase English letters.

## Interview Insight
If the character set is not limited to lowercase English letters, use a `HashMap<Character, Integer>` instead.