# Implement Queue Using Stacks

## Intuition
A queue is FIFO while a stack is LIFO. Use two stacks: `in` for incoming elements and `out` for removals. Move elements from `in` to `out` only when `out` is empty.

## Java
```java
class MyQueue {
    Deque<Integer> in=new ArrayDeque<>(), out=new ArrayDeque<>();
    public void push(int x){in.push(x);}
    public int pop(){peek();return out.pop();}
    public int peek(){if(out.isEmpty())while(!in.isEmpty())out.push(in.pop());return out.peek();}
    public boolean empty(){return in.isEmpty()&&out.isEmpty();}
}
```

## Complexity
Amortized O(1) per operation, O(n) space.