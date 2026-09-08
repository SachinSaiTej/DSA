# Remove K Digits

## Problem
Remove exactly `k` digits from a numeric string to produce the smallest possible number.

## Intuition
Use a monotonic increasing stack. If the current digit is smaller than the stack top, removing the larger previous digit improves the number.

## Java
```java
public String removeKdigits(String num, int k) {
    Deque<Character> st = new ArrayDeque<>();
    for (char c : num.toCharArray()) {
        while (k > 0 && !st.isEmpty() && st.peekLast() > c) {
            st.pollLast(); k--;
        }
        st.addLast(c);
    }
    while (k-- > 0) st.pollLast();
    StringBuilder sb = new StringBuilder();
    boolean leading = true;
    for (char c : st) {
        if (leading && c == '0') continue;
        leading = false; sb.append(c);
    }
    return sb.length() == 0 ? "0" : sb.toString();
}
```

## Complexity
Time O(n), space O(n).