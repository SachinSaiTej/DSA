# Design Circular Queue

## Intuition
Use an array with `front`, `rear`, and `size`. Circular indexing with `(index + 1) % capacity` reuses freed slots.

## Java
```java
class MyCircularQueue{
 int[] a;int front=0,rear=0,size=0;
 MyCircularQueue(int k){a=new int[k];}
 boolean enQueue(int v){if(isFull())return false;a[rear]=v;rear=(rear+1)%a.length;size++;return true;}
 boolean deQueue(){if(isEmpty())return false;front=(front+1)%a.length;size--;return true;}
 int Front(){return isEmpty()?-1:a[front];}
 int Rear(){return isEmpty()?-1:a[(rear-1+a.length)%a.length];}
 boolean isEmpty(){return size==0;} boolean isFull(){return size==a.length;}
}
```

## Complexity
All operations O(1), space O(k).