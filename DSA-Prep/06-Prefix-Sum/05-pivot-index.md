# Pivot Index

## Intuition
Let `left` be the sum before the current index. The index is a pivot when `left == total-left-num`.

## Java
```java
public int pivotIndex(int[] a){int total=0,left=0;for(int x:a)total+=x;for(int i=0;i<a.length;i++){if(left==total-left-a[i])return i;left+=a[i];}return -1;}
```

## Complexity
O(n) time, O(1) space.