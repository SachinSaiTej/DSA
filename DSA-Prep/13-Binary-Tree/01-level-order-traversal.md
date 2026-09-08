# 1. Binary Tree Level Order Traversal

## Problem

Return the nodes of a binary tree level by level, from left to right.

Example:

```text
    3
   / \
  9  20
     / \
    15  7
```

Output: `[[3], [9, 20], [15, 7]]`

## Intuition

Use BFS with a queue. The queue processes nodes level by level. At the start of each level, `queue.size()` tells us exactly how many nodes belong to that level.

## Approach

1. Put the root in a queue.
2. Capture the current queue size.
3. Remove exactly that many nodes and put their values into the current level.
4. Add their children to the queue.
5. Repeat until the queue is empty.

## Java

```java
public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> result = new ArrayList<>();

    if (root == null) return result;

    Queue<TreeNode> queue = new ArrayDeque<>();
    queue.offer(root);

    while (!queue.isEmpty()) {
        int size = queue.size();
        List<Integer> level = new ArrayList<>();

        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();
            level.add(node.val);

            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }

        result.add(level);
    }

    return result;
}
```

## Complexity

- Time: **O(n)**
- Space: **O(n)**

## Interview Point

`size` is the important part: it freezes the current level before its children are added to the queue.
