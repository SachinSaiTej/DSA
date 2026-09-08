# Reverse String

## Problem
Reverse an array of characters in place.

## Intuition
Use two pointers. Swap the characters at the left and right ends and move both toward the center.

## Java
```java
public void reverseString(char[] s) {
    int left = 0, right = s.length - 1;
    while (left < right) {
        char temp = s[left];
        s[left] = s[right];
        s[right] = temp;
        left++;
        right--;
    }
}
```

## Complexity
Time O(n), space O(1).