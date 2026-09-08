# Kth Smallest Element in a BST

## Problem
Return the kth smallest value in a BST.

## Intuition
Inorder traversal of a BST produces values in sorted order. Stop at the kth visited node.

## Java
```java
public int kthSmallest(TreeNode root, int k) {
    Deque<TreeNode> st = new ArrayDeque<>();
    while (true) {
        while (root != null) { st.push(root); root = root.left; }
        root = st.pop();
        if (--k == 0) return root.val;
        root = root.right;
    }
}
```

## Complexity
Time O(h + k), space O(h).