## 104. Maximum Depth of Binary Tree (Easy)
Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Note**: A leaf is a node with no children.

__Example:__
Given binary tree` [3,9,20,null,null,15,7]`,
```
    3
   / \
  9  20
    /  \
   15   7
```
return its depth = 3.

__My Solution:__
```js
var maxDepth = function(root) {
    if(!root) return 0;
    const count = (node) => {
        if(!node) return 0;
        let left = 1 + count(node.left);
        let right = 1 + count(node.right);
        return Math.max(left, right);
    }
    return count(root);
};
```
