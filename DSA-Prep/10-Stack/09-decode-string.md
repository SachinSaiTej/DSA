# Decode String

## Problem
Decode strings such as `3[a2[c]]` into `accaccacc`.

## Intuition
Use stacks for repeat counts and partial strings. On `[` save the current context; on `]` build the repeated string.

## Java
```java
public String decodeString(String s) {
    Deque<Integer> counts = new ArrayDeque<>();
    Deque<StringBuilder> strings = new ArrayDeque<>();
    StringBuilder cur = new StringBuilder();
    int num = 0;
    for (char c : s.toCharArray()) {
        if (Character.isDigit(c)) num = num * 10 + c - '0';
        else if (c == '[') {
            counts.push(num); strings.push(cur); num = 0; cur = new StringBuilder();
        } else if (c == ']') {
            StringBuilder prev = strings.pop();
            int k = counts.pop();
            while (k-- > 0) prev.append(cur);
            cur = prev;
        } else cur.append(c);
    }
    return cur.toString();
}
```

## Complexity
Time O(output size), space O(output size).