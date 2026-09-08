# 14. Binary Tree Left View

## Problem

Return the nodes visible when looking at the tree from the left side, from top to bottom.

## Intuition

Use BFS. At each level, the first node processed is the leftmost visible node.

## Java

```java
public List<Integer> leftSideView(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    if (root == null) return result;

    Queue<TreeNode> queue = new ArrayDeque<>();
    queue.offer(root);

    while (!queue.isEmpty()) {
        int size = queue.size();

        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();

            if (i == 0) result.add(node.val);

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

## Interview Point

Left view = **first node of every level**; right view = **last node of every level**.
