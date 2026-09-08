# 6. Construct Binary Tree from Preorder and Inorder

## Problem

Given preorder and inorder traversals of a binary tree, reconstruct the original tree.

Example:

```text
preorder = [3, 9, 20, 15, 7]
inorder  = [9, 3, 15, 20, 7]
```

The root is `3`; values left of `3` in inorder form the left subtree and values right of it form the right subtree.

## Intuition

Preorder always gives the root first. Use a `HashMap` to find the root's index in inorder in O(1), then recursively build left and right subtrees.

## Java

```java
public TreeNode buildTree(int[] preorder, int[] inorder) {
    Map<Integer, Integer> indexMap = new HashMap<>();

    for (int i = 0; i < inorder.length; i++) {
        indexMap.put(inorder[i], i);
    }

    return build(preorder, 0, preorder.length - 1,
                 inorder, 0, inorder.length - 1, indexMap);
}

private TreeNode build(int[] preorder, int preLeft, int preRight,
                       int[] inorder, int inLeft, int inRight,
                       Map<Integer, Integer> indexMap) {
    if (preLeft > preRight || inLeft > inRight) return null;

    int rootValue = preorder[preLeft];
    TreeNode root = new TreeNode(rootValue);

    int rootIndex = indexMap.get(rootValue);
    int leftSize = rootIndex - inLeft;

    root.left = build(preorder, preLeft + 1, preLeft + leftSize,
                      inorder, inLeft, rootIndex - 1, indexMap);

    root.right = build(preorder, preLeft + leftSize + 1, preRight,
                       inorder, rootIndex + 1, inRight, indexMap);

    return root;
}
```

## Complexity

- Time: **O(n)**
- Space: **O(n)**

## Interview Point

The `leftSize` calculation connects the two traversal arrays and determines the exact preorder ranges for the two recursive calls.
