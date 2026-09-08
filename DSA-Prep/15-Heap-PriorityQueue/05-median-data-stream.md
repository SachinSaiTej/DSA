# Find Median from Data Stream

## Intuition
Use two heaps: a max-heap for the lower half and a min-heap for the upper half. Keep their sizes within one of each other.

## Java
```java
class MedianFinder{PriorityQueue<Integer>lo=new PriorityQueue<>(Collections.reverseOrder()),hi=new PriorityQueue<>();public void addNum(int x){lo.offer(x);hi.offer(lo.poll());if(hi.size()>lo.size())lo.offer(hi.poll());}public double findMedian(){return lo.size()>hi.size()?lo.peek():(lo.peek()+hi.peek())/2.0;}}
```

## Complexity
addNum O(log n), median O(1), space O(n).