## 687. Longest Univalue Path (Easy)
Given a binary tree, find the length of the longest path where each node in the path has the same value. This path may or may not pass through the root.

__Example 1:__
```
              5
             / \
            4   5
           / \   \
          1   1   5
          
return 2;
```
__Example 2:__
```
              1
             / \
            4   5
           / \   \
          4   4   5
          
return 2;
```
__My Solution:__
- I have to update the max before return anything, so checking the value of current node with the value of previous node is after the recursive calls.
```js
var longestUnivaluePath = function(root) {
    let max = 0;
    const dfs = (node, prev) => {
        if(!node) return 0;
        let left = dfs(node.left, node.val);
        let right = dfs(node.right, node.val);
        max = Math.max(left + right, max);
        if(node.val != prev) return 0;
        return 1 + Math.max(left, right);
    }
    dfs(root, null);
    return max;
};
```