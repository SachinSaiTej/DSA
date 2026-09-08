# Remove K Digits

## Problem
Remove exactly `k` digits from a numeric string to produce the smallest possible number.

## Intuition
Use a monotonic increasing stack. If the current digit is smaller than the stack top, removing the larger previous digit makes the resulting number smaller.

## Java
```java
public String removeKdigits(String num, int k) {
    Deque<Character> stack = new ArrayDeque<>();

    for (char c : num.toCharArray()) {
        while (k > 0 && !stack.isEmpty() && stack.peekLast() > c) {
            stack.pollLast();
            k--;
        }

        stack.addLast(c);
    }

    while (k-- > 0) {
        stack.pollLast();
    }

    StringBuilder result = new StringBuilder();
    boolean leadingZero = true;

    for (char c : stack) {
        if (leadingZero && c == '0') {
            continue;
        }

        leadingZero = false;
        result.append(c);
    }

    return result.length() == 0 ? "0" : result.toString();
}
```

## Complexity
Time O(n), space O(n).