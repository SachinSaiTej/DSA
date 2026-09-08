# Recover Binary Search Tree

## Problem
Two nodes of a BST were swapped. Restore the tree without changing its structure.

## Intuition
Inorder traversal should be sorted. Find the two nodes that violate this order and swap their values.

## Java
```java
TreeNode first=null,second=null,prev=null;public void recoverTree(TreeNode root){first=second=prev=null;dfs(root);int t=first.val;first.val=second.val;second.val=t;}void dfs(TreeNode n){if(n==null)return;dfs(n.left);if(prev!=null&&prev.val>n.val){if(first==null)first=prev;second=n;}prev=n;dfs(n.right);}
```

## Complexity
O(n) time and O(h) recursion space.