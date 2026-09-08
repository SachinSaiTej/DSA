# Kth Smallest Element

## Problem
Return the kth smallest value in a Binary Search Tree.

## Intuition
Inorder traversal of a BST visits nodes in ascending order. Use an iterative stack and stop when the kth node is visited.

## Java
```java
public int kthSmallest(TreeNode root, int k) {
    Deque<TreeNode> stack = new ArrayDeque<>();

    while (true) {
        while (root != null) {
            stack.push(root);
            root = root.left;
        }

        root = stack.pop();

        if (--k == 0) {
            return root.val;
        }

        root = root.right;
    }
}
```

## Complexity
Time O(h + k), space O(h), where h is the tree height.