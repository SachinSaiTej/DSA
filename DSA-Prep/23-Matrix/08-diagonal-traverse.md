# Diagonal Traverse

## Problem
Return a matrix's elements in alternating up-right and down-left diagonal order.

## Intuition
Each diagonal has constant `row + col`. Walk diagonals one by one and reverse every other diagonal.

## Java
```java
public int[] findDiagonalOrder(int[][] m){
    if(m.length==0)return new int[0];
    int R=m.length,C=m[0].length;int[]a=new int[R*C];int k=0;
    for(int s=0;s<=R+C-2;s++){
        List<Integer>d=new ArrayList<>();
        int r=Math.min(s,R-1),c=s-r;
        while(r>=0&&c<C){d.add(m[r][c]);r--;c++;}
        if(s%2==0)Collections.reverse(d);
        for(int x:d)a[k++]=x;
    }
    return a;
}
```

## Complexity
Time O(RC), space O(min(R,C)) for a diagonal.