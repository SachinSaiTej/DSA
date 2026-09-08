# Reverse Words in a String

## Problem
Reverse the order of words in a string while removing extra spaces between words.

## Intuition
Trim the string, split it into words, then append those words from right to left. In an interview, explain that an in-place character-array solution is possible if extra space is restricted.

## Java
```java
public String reverseWords(String s) {
    String[] words = s.trim().split("\\s+");
    StringBuilder ans = new StringBuilder();
    for (int i = words.length - 1; i >= 0; i--) {
        if (ans.length() > 0) ans.append(' ');
        ans.append(words[i]);
    }
    return ans.toString();
}
```

## Complexity
Time O(n), space O(n) for the words and output.