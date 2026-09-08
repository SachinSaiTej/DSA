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
    StringBuilder current = new StringBuilder();
    int number = 0;

    for (char c : s.toCharArray()) {
        if (Character.isDigit(c)) {
            number = number * 10 + (c - '0');
        } else if (c == '[') {
            counts.push(number);
            strings.push(current);
            number = 0;
            current = new StringBuilder();
        } else if (c == ']') {
            StringBuilder previous = strings.pop();
            int repeat = counts.pop();

            while (repeat-- > 0) {
                previous.append(current);
            }

            current = previous;
        } else {
            current.append(c);
        }
    }

    return current.toString();
}
```

## Complexity
Time O(output size), space O(output size).