# Sort Colors

## Intuition
Use Dutch National Flag: `0..low-1` are zeroes, `low..mid-1` ones, `high+1..` twos.

## Java
```java
public void sortColors(int[]a){int l=0,m=0,r=a.length-1;while(m<=r){if(a[m]==0){int t=a[l];a[l++]=a[m];a[m++]=t;}else if(a[m]==1)m++;else{int t=a[m];a[m]=a[r];a[r--]=t;}}}
```

## Complexity
O(n) time, O(1) space.