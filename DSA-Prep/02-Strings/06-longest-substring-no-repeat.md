# Longest Substring Without Repeating Characters

## Problem
Find the length of the longest substring containing no repeated characters.

## Intuition
Maintain a sliding window and a map of each character's latest index. When a duplicate appears inside the window, move the left boundary just after its previous occurrence.

## Java
```java
public int lengthOfLongestSubstring(String s) {
    Map<Character, Integer> last = new HashMap<>();
    int left = 0, best = 0;
    for (int right = 0; right < s.length(); right++) {
        char c = s.charAt(right);
        if (last.containsKey(c)) left = Math.max(left, last.get(c) + 1);
        last.put(c, right);
        best = Math.max(best, right - left + 1);
    }
    return best;
}
```

## Complexity
Time O(n), space O(min(n, character-set size)).

## Interview Insight
This is a classic variable-size sliding-window problem.