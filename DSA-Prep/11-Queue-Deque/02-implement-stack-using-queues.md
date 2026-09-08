# Implement Stack Using Queues

## Problem
Implement LIFO stack operations using queue data structures.

## Intuition
For a single queue, after adding a new element, rotate all previous elements behind it. The newest element stays at the front and behaves like a stack top.

## Java
```java
class MyStack {
    Queue<Integer> q = new ArrayDeque<>();
    public void push(int x) {
        q.offer(x);
        for (int i = 0, n = q.size() - 1; i < n; i++) q.offer(q.poll());
    }
    public int pop() { return q.poll(); }
    public int top() { return q.peek(); }
    public boolean empty() { return q.isEmpty(); }
}
```

## Complexity
Push O(n), pop/top O(1), space O(n).