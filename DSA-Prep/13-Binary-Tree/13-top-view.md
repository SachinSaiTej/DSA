# 13. Binary Tree Top View

## Problem

Return the nodes visible when looking at the tree from above, ordered from left to right.

## Intuition

Assign every node a horizontal distance (HD): root `0`, left `-1`, right `+1`. During BFS, the first node encountered at each HD is the top-visible node.

## Java

```java
public List<Integer> topView(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    if (root == null) return result;

    Map<Integer, Integer> map = new TreeMap<>();
    Queue<Pair> queue = new ArrayDeque<>();
    queue.offer(new Pair(root, 0));

    while (!queue.isEmpty()) {
        Pair p = queue.poll();
        if (!map.containsKey(p.column)) {
            map.put(p.column, p.node.val);
        }

        if (p.node.left != null)
            queue.offer(new Pair(p.node.left, p.column - 1));
        if (p.node.right != null)
            queue.offer(new Pair(p.node.right, p.column + 1));
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

Top view keeps only the **first BFS node per horizontal distance**.
