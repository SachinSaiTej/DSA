# Convert Sorted Array to BST

## Intuition
Choose the middle element as root so the left and right halves remain balanced. Recursively build both subtrees.

## Java
```java
public TreeNode sortedArrayToBST(int[]a){return build(a,0,a.length-1);}TreeNode build(int[]a,int l,int r){if(l>r)return null;int m=l+(r-l)/2;TreeNode n=new TreeNode(a[m]);n.left=build(a,l,m-1);n.right=build(a,m+1,r);return n;}
```

## Complexity
O(n) time and O(log n) stack for a balanced tree.