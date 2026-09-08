# Longest Common Prefix

## Problem
Find the longest prefix shared by every string in an array.

## Intuition
Start with the first string as the candidate prefix. Compare it with every other string and shorten it until it matches the beginning of that string.

## Java
```java
public String longestCommonPrefix(String[] strs) {
    if (strs.length == 0) return "";
    String prefix = strs[0];
    for (int i = 1; i < strs.length; i++) {
        while (!strs[i].startsWith(prefix)) {
            prefix = prefix.substring(0, prefix.length() - 1);
            if (prefix.isEmpty()) return "";
        }
    }
    return prefix;
}
```

## Complexity
Time O(total characters examined), space O(1) excluding temporary strings.

## Interview Insight
A character-by-character scan column-wise is another clean O(total input size) approach.