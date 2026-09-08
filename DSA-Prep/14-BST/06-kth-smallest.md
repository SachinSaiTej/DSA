# Kth Smallest Element

## Intuition
Inorder traversal of a BST visits nodes in ascending order. Use an iterative stack and stop at the kth node.

## Java
```java
public int kthSmallest(TreeNode r,int k){Deque<TreeNode>s=new ArrayDeque<>();while(true){while(r!=null){s.push(r);r=r.left;}r=s.pop();if(--k==0)return r.val;r=r.right;}}
```

## Complexity
O(h+k) time and O(h) space.