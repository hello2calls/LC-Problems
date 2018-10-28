## 543. Diameter of Binary Tree (Easy)
Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the **longest** path between any two nodes in a tree. This path may or may not pass through the root.

__Example:__
```
          1
         / \
        2   3
       / \     
      4   5    
      
Return 3, which is the length of the path [4,2,1,3] or [5,2,1,3].
```

__My Solution:__
- in the call on every node, I need to update the max without adding the current node, but I need to return the max of current node's left and right and adding current node itself.
```js
var diameterOfBinaryTree = function(root) {
    let max = 0;
    const dfs = (node) => {
        if(!node) return 0;
        let left = dfs(node.left);
        let right = dfs(node.right);
        max = Math.max(max, left + right);
        return Math.max(left, right) + 1;
    }
    dfs(root);
    return max;
};
```