# Valid Parentheses

## Problem
Determine whether brackets `()[]{}` are correctly opened and closed.

## Intuition
Push opening brackets onto a stack. When a closing bracket appears, the top of the stack must be its matching opening bracket.

## Java
```java
public boolean isValid(String s) {
    Deque<Character> stack = new ArrayDeque<>();

    for (char c : s.toCharArray()) {
        if (c == '(' || c == '[' || c == '{') {
            stack.push(c);
        } else {
            if (stack.isEmpty()) {
                return false;
            }

            char open = stack.pop();
            if ((c == ')' && open != '(')
                    || (c == ']' && open != '[')
                    || (c == '}' && open != '{')) {
                return false;
            }
        }
    }

    return stack.isEmpty();
}
```

## Complexity
Time O(n), space O(n).