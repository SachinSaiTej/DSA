# 15. Binary Tree Vertical Traversal

## Problem

Group tree nodes by vertical column. Order columns from left to right; within a column order nodes by row from top to bottom. If nodes share the same row and column, sort them by value.

## Intuition

Track `(row, column, value)` for every node. Then sort by `column → row → value` and group by column.

## Java

```java
public List<List<Integer>> verticalTraversal(TreeNode root) {
    List<int[]> nodes = new ArrayList<>();
    dfs(root, 0, 0, nodes);

    nodes.sort((a, b) -> {
        if (a[1] != b[1]) return Integer.compare(a[1], b[1]);
        if (a[0] != b[0]) return Integer.compare(a[0], b[0]);
        return Integer.compare(a[2], b[2]);
    });

    List<List<Integer>> result = new ArrayList<>();
    int previousColumn = Integer.MIN_VALUE;

    for (int[] node : nodes) {
        int column = node[1];
        if (column != previousColumn) {
            result.add(new ArrayList<>());
            previousColumn = column;
        }
        result.get(result.size() - 1).add(node[2]);
    }

    return result;
}

private void dfs(TreeNode node, int row, int column, List<int[]> nodes) {
    if (node == null) return;

    nodes.add(new int[]{row, column, node.val});
    dfs(node.left, row + 1, column - 1, nodes);
    dfs(node.right, row + 1, column + 1, nodes);
}
```

## Complexity

- Time: **O(n log n)**
- Space: **O(n)**

## Interview Point

This is stricter than standard vertical order: same row + same column requires value sorting.
