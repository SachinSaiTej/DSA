# Is Subsequence

## Problem
Determine whether string `s` is a subsequence of string `t`.

## Intuition
Walk through both strings with two pointers. When characters match, advance the pointer in `s`; always advance through `t`.

## Java
```java
public boolean isSubsequence(String s, String t) {
    int i = 0;
    for (int j = 0; j < t.length() && i < s.length(); j++) {
        if (s.charAt(i) == t.charAt(j)) i++;
    }
    return i == s.length();
}
```

## Complexity
Time O(n), space O(1).