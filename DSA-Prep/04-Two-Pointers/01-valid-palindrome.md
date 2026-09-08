# Valid Palindrome

## Problem
Determine whether a string is a palindrome after ignoring non-alphanumeric characters and case.

## Intuition
Use two pointers at the ends. Skip characters that are not letters or digits, then compare the remaining characters case-insensitively.

## Java
```java
public boolean isPalindrome(String s) {
    int l = 0, r = s.length() - 1;
    while (l < r) {
        while (l < r && !Character.isLetterOrDigit(s.charAt(l))) l++;
        while (l < r && !Character.isLetterOrDigit(s.charAt(r))) r--;
        if (Character.toLowerCase(s.charAt(l)) != Character.toLowerCase(s.charAt(r))) return false;
        l++; r--;
    }
    return true;
}
```

## Complexity
Time O(n), space O(1).