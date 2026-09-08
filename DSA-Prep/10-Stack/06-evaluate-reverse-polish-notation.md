# Evaluate Reverse Polish Notation

## Problem
Evaluate an arithmetic expression written in postfix notation.

## Intuition
Numbers go onto a stack. An operator pops the right operand, then the left operand, computes the result, and pushes it back.

## Java
```java
public int evalRPN(String[] tokens) {
    Deque<Integer> stack = new ArrayDeque<>();
    for (String token : tokens) {
        if (token.equals("+") || token.equals("-") || token.equals("*") || token.equals("/")) {
            int b = stack.pop(), a = stack.pop();
            switch (token) {
                case "+" -> stack.push(a + b);
                case "-" -> stack.push(a - b);
                case "*" -> stack.push(a * b);
                default -> stack.push(a / b);
            }
        } else stack.push(Integer.parseInt(token));
    }
    return stack.pop();
}
```

## Complexity
Time O(n), space O(n).