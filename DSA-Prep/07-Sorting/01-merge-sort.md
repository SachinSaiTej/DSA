# Merge Sort

## Intuition
Divide the array into halves, recursively sort both halves, then merge the sorted halves.

## Java
```java
void mergeSort(int[] a,int l,int r){if(l>=r)return;int m=l+(r-l)/2;mergeSort(a,l,m);mergeSort(a,m+1,r);merge(a,l,m,r);}void merge(int[]a,int l,int m,int r){int[]t=new int[r-l+1];int i=l,j=m+1,k=0;while(i<=m&&j<=r)t[k++]=a[i]<=a[j]?a[i++]:a[j++];while(i<=m)t[k++]=a[i++];while(j<=r)t[k++]=a[j++];System.arraycopy(t,0,a,l,t.length);}
```

## Complexity
O(n log n) time, O(n) space.