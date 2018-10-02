## 226. Invert Binary Tree (Easy)
Invert a binary tree.

**Example:**
Input:
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```
Output:
```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

__My Solution:__
```js
var invertTree = function(root) {
    if(!root) [];
    const invert = (node) => {
        if(!node) return;
        let left = node.left;
        let right = node.right;
        node.left = right;
        node.right = left;
        invert(left);
        invert(right);
    }
    invert(root);
    return root;
};
```
