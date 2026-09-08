# Range Addition

## Intuition
Apply each range increment using difference-array boundary updates, then take a prefix sum to obtain the final values.

## Java
```java
public int[] getModifiedArray(int length,int[][] updates){int[] d=new int[length+1];for(int[] u:updates){d[u[0]]+=u[2];d[u[1]+1]-=u[2];}int[] a=new int[length];for(int i=0,cur=0;i<length;i++){cur+=d[i];a[i]=cur;}return a;}
```

## Complexity
O(length + updates) time, O(length) space.