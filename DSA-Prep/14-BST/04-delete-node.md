# Delete Node in a BST

## Problem
Given the root of a BST and a key, delete the node containing that key and return the root.

## Intuition
Use the BST property to search for the key. Once found, handle three cases:

1. No children: remove the node.
2. One child: replace the node with its child.
3. Two children: replace its value with the inorder successor, then delete the successor.

## Java
```java
public TreeNode deleteNode(TreeNode root, int key) {
    if (root == null) {
        return null;
    }

    if (key < root.val) {
        root.left = deleteNode(root.left, key);
    } else if (key > root.val) {
        root.right = deleteNode(root.right, key);
    } else {
        if (root.left == null) {
            return root.right;
        }

        if (root.right == null) {
            return root.left;
        }

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
Time O(h), space O(h) from recursion.