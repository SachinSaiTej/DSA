# Last Stone Weight

## Intuition
Always smash the two heaviest stones. A max-heap gives those stones in O(log n).

## Java
```java
public int lastStoneWeight(int[]a){PriorityQueue<Integer>q=new PriorityQueue<>(Collections.reverseOrder());for(int x:a)q.offer(x);while(q.size()>1){int x=q.poll()-q.poll();if(x>0)q.offer(x);}return q.isEmpty()?0:q.peek();}
```

## Complexity
O(n log n) time and O(n) space.