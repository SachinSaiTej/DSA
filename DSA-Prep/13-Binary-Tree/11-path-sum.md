# 11. Path Sum

## Problem

Determine whether there is a **root-to-leaf** path whose node values sum to `targetSum`.

Example: for the path `5 → 4 → 11 → 2`, the sum is `22`, so `targetSum = 22` returns `true`.

## Intuition

Subtract the current node value from the remaining target. At a leaf, check whether the remaining target equals the leaf value.

## Java

```java
public boolean hasPathSum(TreeNode root, int targetSum) {
    if (root == null) return false;

    if (root.left == null && root.right == null) {
        return root.val == targetSum;
    }

    int remaining = targetSum - root.val;
    return hasPathSum(root.left, remaining)
        || hasPathSum(root.right, remaining);
}
```

## Complexity

- Time: **O(n)**
- Space: **O(h)**

## Interview Point

The word **leaf** matters. A path ending at an internal node does not count.
