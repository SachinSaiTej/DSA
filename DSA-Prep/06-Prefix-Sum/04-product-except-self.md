# Product of Array Except Self

## Intuition
For each index, multiply the product of everything to its left by the product of everything to its right. Use the output array for the left product and a running variable for the right product.

## Java
```java
public int[] productExceptSelf(int[] a){int n=a.length;int[] out=new int[n];out[0]=1;for(int i=1;i<n;i++)out[i]=out[i-1]*a[i-1];int right=1;for(int i=n-1;i>=0;i--){out[i]*=right;right*=a[i];}return out;}
```

## Complexity
O(n) time, O(1) extra space excluding output.