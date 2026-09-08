# Validate Binary Search Tree

## Problem
Determine whether a binary tree satisfies strict BST ordering.

## Intuition
Every node must lie inside a valid `(lower, upper)` range inherited from its ancestors.

## Java
```java
public boolean isValidBST(TreeNode root) {
    return valid(root, Long.MIN_VALUE, Long.MAX_VALUE);
}
private boolean valid(TreeNode n, long low, long high) {
    if (n == null) return true;
    if (n.val <= low || n.val >= high) return false;
    return valid(n.left, low, n.val) && valid(n.right, n.val, high);
}
```

## Complexity
Time O(n), space O(h).