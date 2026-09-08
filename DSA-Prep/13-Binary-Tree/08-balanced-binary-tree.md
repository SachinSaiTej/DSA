# 8. Balanced Binary Tree

## Problem

Determine whether the tree is height-balanced: at every node, the difference between left and right subtree heights is at most 1.

## Intuition

Compute heights bottom-up. Return `-1` as a sentinel as soon as an unbalanced subtree is found, avoiding repeated height calculations.

## Java

```java
public boolean isBalanced(TreeNode root) {
    return height(root) != -1;
}

private int height(TreeNode node) {
    if (node == null) return 0;

    int left = height(node.left);
    if (left == -1) return -1;

    int right = height(node.right);
    if (right == -1) return -1;

    if (Math.abs(left - right) > 1) return -1;

    return 1 + Math.max(left, right);
}
```

## Complexity

- Time: **O(n)**
- Space: **O(h)**

## Interview Point

The `-1` sentinel turns a potentially O(n²) repeated-height solution into O(n).
