# Search in a BST

## Problem
Find a node with a given value in a binary search tree.

## Intuition
BST ordering tells us which subtree can contain the value: go left if target is smaller, otherwise right.

## Java
```java
public TreeNode searchBST(TreeNode root, int val) {
    while (root != null && root.val != val) {
        root = (val < root.val) ? root.left : root.right;
    }
    return root;
}
```

## Complexity
Time O(h), space O(1).