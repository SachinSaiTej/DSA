# 9. Binary Tree Right Side View

## Problem

Return the nodes visible when looking at a binary tree from the right side.

Example:

```text
      1
     / \
    2   3
     \   \
      5   4
```

Output: `[1, 3, 4]`.

## Intuition

Use BFS and process one level at a time. The last node processed in each level is the rightmost visible node.

## Java

```java
public List<Integer> rightSideView(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    if (root == null) return result;

    Queue<TreeNode> queue = new ArrayDeque<>();
    queue.offer(root);

    while (!queue.isEmpty()) {
        int size = queue.size();

        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();

            if (i == size - 1) result.add(node.val);

            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }
    }

    return result;
}
```

## Complexity

- Time: **O(n)**
- Space: **O(n)**
