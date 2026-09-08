# 10. Maximum Difference Between Node and Ancestor

## Problem

For every node, consider its ancestors. Find the maximum absolute difference between a node and any ancestor.

## Intuition

While traversing downward, keep the minimum and maximum values seen on the current root-to-node path. The largest possible difference is `max - min`.

## Java

```java
public int maxAncestorDiff(TreeNode root) {
    return dfs(root, root.val, root.val);
}

private int dfs(TreeNode node, int min, int max) {
    if (node == null) return max - min;

    min = Math.min(min, node.val);
    max = Math.max(max, node.val);

    return Math.max(dfs(node.left, min, max),
                   dfs(node.right, min, max));
}
```

## Complexity

- Time: **O(n)**
- Space: **O(h)**
