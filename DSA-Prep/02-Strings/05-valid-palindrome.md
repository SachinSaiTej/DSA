# Valid Palindrome

## Problem
Determine whether a string is a palindrome after ignoring non-alphanumeric characters and case.

## Intuition
Use two pointers from both ends. Skip characters that are not alphanumeric, then compare lowercase versions.

## Java
```java
public boolean isPalindrome(String s) {
    int left = 0, right = s.length() - 1;
    while (left < right) {
        while (left < right && !Character.isLetterOrDigit(s.charAt(left))) left++;
        while (left < right && !Character.isLetterOrDigit(s.charAt(right))) right--;
        if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) return false;
        left++;
        right--;
    }
    return true;
}
```

## Complexity
Time O(n), space O(1).