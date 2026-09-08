# 2. Diameter of Binary Tree

## Problem

Find the diameter: the longest path between any two nodes. The path does not have to pass through the root. Return the number of edges.

Example:

```text
      1
     / \
    2   3
   / \
  4   5
```

Longest path: `4 → 2 → 1 → 3`, so the answer is `3`.

## Intuition

For every node, the longest path passing through that node is `leftHeight + rightHeight`. While calculating heights bottom-up, update a global maximum.

## Java

```java
private int diameter = 0;

public int diameterOfBinaryTree(TreeNode root) {
    depth(root);
    return diameter;
}

private int depth(TreeNode node) {
    if (node == null) return 0;

    int left = depth(node.left);
    int right = depth(node.right);

    diameter = Math.max(diameter, left + right);

    return 1 + Math.max(left, right);
}
```

## Complexity

- Time: **O(n)**
- Space: **O(h)**

## Interview Point

Return height to the parent, but use `left + right` only for the diameter candidate at the current node.
