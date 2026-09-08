# 7. Invert Binary Tree

## Problem

Swap the left and right children of every node.

Example:

```text
    4                 4
   / \               / \
  2   7     →       7   2
 / \ / \           / \ / \
1  3 6  9           9  6 3  1
```

## Intuition

At every node, recursively invert the two subtrees and swap them.

## Java

```java
public TreeNode invertTree(TreeNode root) {
    if (root == null) return null;

    TreeNode temp = root.left;
    root.left = invertTree(root.right);
    root.right = invertTree(temp);

    return root;
}
```

## Complexity

- Time: **O(n)**
- Space: **O(h)**
