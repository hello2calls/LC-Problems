## 872. Leaf-Similar Trees (Easy)
Consider all the leaves of a binary tree.  From left to right order, the values of those leaves form a leaf value sequence.
![](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/16/tree.png)

For example, in the given tree above, the leaf value sequence is `(6, 7, 4, 9, 8)`.

Two binary trees are considered leaf-similar if their leaf value sequence is the same.

Return `true` if and only if the two given trees with head nodes `root1` and `root2` are leaf-similar.

__My Solution:__
- in-order traverse
- going to the very bottom left first, then the middle, then the right.
```js
var leafSimilar = function(root1, root2) {

    const dfs = (node, str = "") => {
        if (!node) return '';
        str += dfs(node.left);
        if (!node.left && !node.right) return node.val;
        str += dfs(node.right);
        return str;
    }
    return dfs(root1) === dfs(root2);
};
```
