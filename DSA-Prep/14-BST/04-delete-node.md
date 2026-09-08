# Delete Node in BST

## Intuition
Find the node. If it has at most one child, replace it with that child. With two children, replace its value with the inorder successor (minimum of the right subtree), then delete that successor.

## Java
```java
public TreeNode deleteNode(TreeNode r,int key){if(r==null)return null;if(key<r.val)r.left=deleteNode(r.left,key);else if(key>r.val)r.right=deleteNode(r.right,key);else{if(r.left==null)return r.right;if(r.right==null)return r.left;TreeNode s=r.right;while(s.left!=null)s=s.left;r.val=s.val;r.right=deleteNode(r.right,s.val);}return r;}
```

## Complexity
O(h) time and O(h) recursive space.