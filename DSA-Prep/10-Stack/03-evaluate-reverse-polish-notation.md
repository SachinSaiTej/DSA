# Evaluate Reverse Polish Notation

## Problem
Evaluate an arithmetic expression written in postfix notation.

## Intuition
Numbers go onto a stack. When an operator appears, pop the right operand first, then the left operand, perform the operation, and push the result back.

## Java
```java
public int evalRPN(String[] tokens) {
    Deque<Integer> stack = new ArrayDeque<>();

    for (String token : tokens) {
        if (token.equals("+") || token.equals("-")
                || token.equals("*") || token.equals("/")) {
            int right = stack.pop();
            int left = stack.pop();

            switch (token) {
                case "+" -> stack.push(left + right);
                case "-" -> stack.push(left - right);
                case "*" -> stack.push(left * right);
                default -> stack.push(left / right);
            }
        } else {
            stack.push(Integer.parseInt(token));
        }
    }

    return stack.pop();
}
```

## Complexity
Time O(n), space O(n).