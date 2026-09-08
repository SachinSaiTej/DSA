# Insert into a BST

## Intuition
Follow the BST property until reaching a null child, then attach the new node there.

## Java
```java
public TreeNode insertIntoBST(TreeNode root,int val){if(root==null)return new TreeNode(val);if(val<root.val)root.left=insertIntoBST(root.left,val);else root.right=insertIntoBST(root.right,val);return root;}
```

## Complexity
O(h) time and O(h) recursive space.