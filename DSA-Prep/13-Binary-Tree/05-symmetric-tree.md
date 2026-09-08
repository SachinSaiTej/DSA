# 5. Symmetric Tree

## Problem

Determine whether a binary tree is a mirror of itself around its center.

Example:

```text
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

Output: `true`.

## Intuition

Compare two subtrees in mirror order. The left child of one side must match the right child of the other, and vice versa.

## Java

```java
public boolean isSymmetric(TreeNode root) {
    if (root == null) return true;
    return isMirror(root.left, root.right);
}

private boolean isMirror(TreeNode left, TreeNode right) {
    if (left == null && right == null) return true;
    if (left == null || right == null || left.val != right.val) return false;

    return isMirror(left.left, right.right)
        && isMirror(left.right, right.left);
}
```

## Complexity

- Time: **O(n)**
- Space: **O(h)**

## Interview Point

The recursive comparisons cross over: `left.left ↔ right.right` and `left.right ↔ right.left`.
