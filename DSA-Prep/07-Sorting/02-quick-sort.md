# Quick Sort

## Intuition
Partition around a pivot so smaller values go left and larger values right, then recursively sort both partitions.

## Java
```java
void quickSort(int[]a,int l,int r){if(l>=r)return;int p=partition(a,l,r);quickSort(a,l,p-1);quickSort(a,p+1,r);}int partition(int[]a,int l,int r){int p=a[r],i=l;for(int j=l;j<r;j++)if(a[j]<=p){int t=a[i];a[i++]=a[j];a[j]=t;}int t=a[i];a[i]=a[r];a[r]=t;return i;}
```

## Complexity
Average O(n log n), worst O(n²), O(log n) average recursion space.