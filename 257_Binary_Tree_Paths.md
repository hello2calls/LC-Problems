## 257. Binary Tree Paths (Easy)
Given a binary tree, return all root-to-leaf paths.

__Example:__
```
Input:

   1
 /   \
2     3
 \
  5

Output: ["1->2->5", "1->3"]

Explanation: All root-to-leaf paths are: 1->2->5, 1->3
```
__My Solution:__
```js
var binaryTreePaths = function(root) {
    if(!root) return [];
    let result = [];
    const dfs = (node, path) => {
        if(!(node.left || node.right)) {
            result.push(path);
            return;
        }
        if(node.left) dfs(node.left, path+`->${node.left.val}`);
        if(node.right) dfs(node.right, path+`->${node.right.val}`);
    }
    dfs(root, `${root.val}`);
    return result;
};
```