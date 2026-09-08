# Longest Palindromic Substring

## Problem
Find the longest substring that is a palindrome.

## Intuition
Every palindrome has a center. Try every character as an odd-length center and every gap as an even-length center, expanding while the characters match.

## Java
```java
public String longestPalindrome(String s) {
    if (s.length() < 2) return s;
    int start = 0, end = 0;
    for (int i = 0; i < s.length(); i++) {
        int odd = expand(s, i, i);
        int even = expand(s, i, i + 1);
        int len = Math.max(odd, even);
        if (len > end - start + 1) {
            start = i - (len - 1) / 2;
            end = i + len / 2;
        }
    }
    return s.substring(start, end + 1);
}

private int expand(String s, int left, int right) {
    while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
        left--;
        right++;
    }
    return right - left - 1;
}
```

## Complexity
Time O(n²), space O(1) excluding output.