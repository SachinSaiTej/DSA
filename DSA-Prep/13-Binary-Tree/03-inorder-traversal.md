# 3. Binary Tree Inorder Traversal

## Problem

Return nodes in **Left → Root → Right** order.

Example:

```text
    1
     \
      2
     /
    3
```

Output: `[1, 3, 2]`

## Intuition

Inorder means completely process the left subtree, then the current node, then the right subtree.

## Java — Recursive

```java
public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    inorder(root, result);
    return result;
}

private void inorder(TreeNode node, List<Integer> result) {
    if (node == null) return;

    inorder(node.left, result);
    result.add(node.val);
    inorder(node.right, result);
}
```

## Complexity

- Time: **O(n)**
- Space: **O(h)**

## Interview Point

For a BST, inorder traversal produces values in sorted order.
