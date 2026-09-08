# 1. Delete Node in a BST

## Problem

Given the root of a BST and a key, delete the node containing that key and return the root.

There are three cases:

1. **Leaf:** remove it.
2. **One child:** replace it with its child.
3. **Two children:** replace its value with the inorder successor (smallest node in the right subtree), then delete that successor.

## Intuition

Use the BST property to search left or right until the key is found. Once found, handle the three structural cases. For two children, the inorder successor preserves BST ordering.

## Java

```java
public TreeNode deleteNode(TreeNode root, int key) {
    if (root == null) return null;

    if (key < root.val) {
        root.left = deleteNode(root.left, key);
    } else if (key > root.val) {
        root.right = deleteNode(root.right, key);
    } else {
        if (root.left == null) return root.right;
        if (root.right == null) return root.left;

        TreeNode successor = root.right;
        while (successor.left != null) {
            successor = successor.left;
        }

        root.val = successor.val;
        root.right = deleteNode(root.right, successor.val);
    }

    return root;
}
```

## Complexity

- Time: **O(h)**
- Space: **O(h)** from recursion.

## Interview Point

For two children, use the **minimum node in the right subtree** (or maximum node in the left subtree) as the replacement.
