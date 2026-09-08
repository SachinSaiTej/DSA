# Find the Middle Index

## Intuition
This is the same balance condition as pivot index: sum on the left must equal sum on the right.

## Java
```java
public int findMiddleIndex(int[] a){int total=0,left=0;for(int x:a)total+=x;for(int i=0;i<a.length;i++){if(left==total-left-a[i])return i;left+=a[i];}return -1;}
```

## Complexity
O(n) time, O(1) space.