# Valid Anagram

## Problem
Determine whether two strings contain exactly the same characters with the same frequencies.

## Intuition
Count each character in the first string and subtract counts while scanning the second. Every count must finish at zero.

## Java
```java
public boolean isAnagram(String s, String t) {
    if (s.length() != t.length()) return false;
    Map<Character, Integer> freq = new HashMap<>();
    for (char c : s.toCharArray()) freq.merge(c, 1, Integer::sum);
    for (char c : t.toCharArray()) {
        int count = freq.getOrDefault(c, 0);
        if (count == 0) return false;
        freq.put(c, count - 1);
    }
    return true;
}
```

## Complexity
Time O(n), space O(k), where k is the character set size.