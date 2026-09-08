# Range Sum Query

## Intuition
Build prefix sums so any range sum is the difference of two prefix values.

## Java
```java
class NumArray{int[] p;NumArray(int[] a){p=new int[a.length+1];for(int i=0;i<a.length;i++)p[i+1]=p[i]+a[i];}public int sumRange(int l,int r){return p[r+1]-p[l];}}
```

## Complexity
Build O(n), query O(1), space O(n).