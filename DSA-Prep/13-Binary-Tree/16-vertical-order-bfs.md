# 16. Binary Tree Vertical Order via BFS

## Problem

Group nodes by horizontal distance from the root and return columns from left to right. For a standard BFS vertical order, nodes in the same column are kept in BFS top-to-bottom order.

## Intuition

Use BFS with `(node, column)`. Root is column `0`; left decreases the column and right increases it. A `TreeMap` keeps columns sorted automatically.

## Java

```java
public List<List<Integer>> verticalOrder(TreeNode root) {
    List<List<Integer>> result = new ArrayList<>();
    if (root == null) return result;

    Map<Integer, List<Integer>> map = new TreeMap<>();
    Queue<Pair> queue = new ArrayDeque<>();
    queue.offer(new Pair(root, 0));

    while (!queue.isEmpty()) {
        Pair current = queue.poll();
        map.computeIfAbsent(current.column, k -> new ArrayList<>())
           .add(current.node.val);

        if (current.node.left != null)
            queue.offer(new Pair(current.node.left, current.column - 1));
        if (current.node.right != null)
            queue.offer(new Pair(current.node.right, current.column + 1));
    }

    result.addAll(map.values());
    return result;
}

static class Pair {
    TreeNode node;
    int column;

    Pair(TreeNode node, int column) {
        this.node = node;
        this.column = column;
    }
}
```

## Complexity

- Time: **O(n log n)** with `TreeMap`
- Space: **O(n)**

## Interview Point

BFS matters because it naturally preserves top-to-bottom ordering. Do not add value sorting unless the interviewer specifies the stricter vertical traversal variant.
