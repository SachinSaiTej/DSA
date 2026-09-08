# 4. Binary Tree Maximum Path Sum

## Problem

Find the maximum path sum in a binary tree. A path may start and end at any nodes but must follow parent-child connections.

Example:

```text
      -10
      /  \
     9   20
        /  \
       15   7
```

Maximum path: `15 → 20 → 7`, answer `42`.

## Intuition

At each node, the best path that uses the node as its highest point is `node + leftGain + rightGain`. But when returning to the parent, we can only return one side.

Negative subtree gains should be ignored with `Math.max(0, gain)`.

## Java

```java
private int maxSum = Integer.MIN_VALUE;

public int maxPathSum(TreeNode root) {
    maxGain(root);
    return maxSum;
}

private int maxGain(TreeNode node) {
    if (node == null) return 0;

    int left = Math.max(0, maxGain(node.left));
    int right = Math.max(0, maxGain(node.right));

    maxSum = Math.max(maxSum, node.val + left + right);

    return node.val + Math.max(left, right);
}
```

## Complexity

- Time: **O(n)**
- Space: **O(h)**

## Interview Point

Do not confuse the value returned to the parent with the global answer. The returned path must be one-sided; the global candidate can use both sides.
