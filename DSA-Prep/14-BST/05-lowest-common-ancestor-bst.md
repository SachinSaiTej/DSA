# Lowest Common Ancestor of a BST

## Problem
Find the lowest node that is an ancestor of two given values in a BST.

## Intuition
If both values are smaller, go left. If both are larger, go right. Otherwise the current node is the split point and is the LCA.

## Java
```java
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    while (root != null) {
        if (p.val < root.val && q.val < root.val) root = root.left;
        else if (p.val > root.val && q.val > root.val) root = root.right;
        else return root;
    }
    return null;
}
```

## Complexity
Time O(h), space O(1).