# Minimum Window Substring

## Problem
Given strings `s` and `t`, find the smallest substring of `s` containing every character of `t` with the required multiplicity.

## Intuition
Use a variable-size sliding window. Expand the right side until the window contains all required characters, then shrink from the left while it remains valid. Keep the smallest valid window.

## Java
```java
public String minWindow(String s, String t) {
    if (t.length() > s.length()) return "";
    int[] need = new int[128];
    for (char c : t.toCharArray()) need[c]++;
    int missing = t.length(), left = 0, bestStart = 0, bestLen = Integer.MAX_VALUE;

    for (int right = 0; right < s.length(); right++) {
        char c = s.charAt(right);
        if (need[c] > 0) missing--;
        need[c]--;

        while (missing == 0) {
            if (right - left + 1 < bestLen) {
                bestLen = right - left + 1;
                bestStart = left;
            }
            char remove = s.charAt(left++);
            need[remove]++;
            if (need[remove] > 0) missing++;
        }
    }
    return bestLen == Integer.MAX_VALUE ? "" : s.substring(bestStart, bestStart + bestLen);
}
```

## Complexity
Time O(n + m), space O(1) for the fixed ASCII alphabet.

## Interview Insight
The key invariant is: when `missing == 0`, the current window contains all required characters, so shrinking from the left finds the minimum valid window ending at `right`.