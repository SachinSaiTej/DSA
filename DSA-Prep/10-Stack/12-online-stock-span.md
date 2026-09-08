# Online Stock Span

## Intuition
Maintain a decreasing stack of `(price, span)`. For a new price, pop all lower/equal prices and add their spans.

## Java
```java
class StockSpanner{Deque<int[]>s=new ArrayDeque<>();public int next(int price){int span=1;while(!s.isEmpty()&&s.peek()[0]<=price)span+=s.pop()[1];s.push(new int[]{price,span});return span;}}
```

## Complexity
O(1) amortized per call, O(n) space.