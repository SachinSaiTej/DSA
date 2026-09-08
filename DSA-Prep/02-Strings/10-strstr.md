# Implement strStr

## Problem
Return the index of the first occurrence of `needle` in `haystack`, or `-1` if it does not occur.

## Intuition
The straightforward solution checks every possible starting position. Compare the substring of length `needle.length()` against `needle`.

## Java
```java
public int strStr(String haystack, String needle) {
    if (needle.isEmpty()) return 0;
    for (int i = 0; i + needle.length() <= haystack.length(); i++) {
        int j = 0;
        while (j < needle.length() && haystack.charAt(i + j) == needle.charAt(j)) j++;
        if (j == needle.length()) return i;
    }
    return -1;
}
```

## Complexity
Time O(nm) worst case, space O(1).

## Interview Insight
For optimal pattern matching, discuss KMP, which reduces the search to O(n + m).