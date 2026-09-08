# 12. Binary Tree Postorder Traversal

## Problem

Return nodes in **Left → Right → Root** order.

Example:

```text
      1
     / \
    2   3
   / \
  4   5
```

Output: `[4, 5, 2, 3, 1]`.

## Intuition

A recursive solution is straightforward, but the iterative version uses a stack and a `lastVisited` pointer to know whether a right subtree has already been processed.

## Java — Iterative

```java
public List<Integer> postorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    if (root == null) return result;

    Deque<TreeNode> stack = new ArrayDeque<>();
    TreeNode curr = root;
    TreeNode lastVisited = null;

    while (curr != null || !stack.isEmpty()) {
        while (curr != null) {
            stack.push(curr);
            curr = curr.left;
        }

        TreeNode node = stack.peek();

        if (node.right != null && node.right != lastVisited) {
            curr = node.right;
        } else {
            result.add(node.val);
            lastVisited = stack.pop();
        }
    }

    return result;
}
```

## Complexity

- Time: **O(n)**
- Space: **O(h)**
