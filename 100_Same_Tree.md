## 100. Same Tree (Easy)
Given two binary trees, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical and the nodes have the same value.

__Example 1:__
```
Input:     1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

Output: true
```
__Example 2:__
```
Input:     1         1
          /           \
         2             2

        [1,2],     [1,null,2]

Output: false
```

__My Solution:__
```js
var isSameTree = function(p, q) {
    if(p === null && q === null) return true;
    if(!(p && q)) return false;
    if(p.val !== q.val) return false;
    
    let left = isSameTree(p.left, q.left);
    let right = isSameTree(p.right, q.right);
    return left && right
};
```