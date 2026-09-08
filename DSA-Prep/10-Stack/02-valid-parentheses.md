# Valid Parentheses

## Problem
Determine whether brackets `()[]{}` are correctly opened and closed.

## Intuition
Push opening brackets. For a closing bracket, the top must be its matching opener.

## Java
```java
public boolean isValid(String s) {
    Deque<Character> stack = new ArrayDeque<>();
    for (char c : s.toCharArray()) {
        if (c == '(' || c == '[' || c == '{') stack.push(c);
        else {
            if (stack.isEmpty()) return false;
            char open = stack.pop();
            if ((c == ')' && open != '(') || (c == ']' && open != '[') || (c == '}' && open != '{')) return false;
        }
    }
    return stack.isEmpty();
}
```

## Complexity
Time O(n), space O(n).