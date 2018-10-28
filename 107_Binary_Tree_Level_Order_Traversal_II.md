## 107. Binary Tree Level Order Traversal II (Easy)
Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

__Example:__
```
    3
   / \
  9  20
    /  \
   15   7

return:
[
  [15,7],
  [9,20],
  [3]
]
```
__My Solution:__
```js
var levelOrderBottom = function(root) {
    if(!root) return [];
    let result = [];
    let que = [root];
    while(que.length > 0){
        let arr = [];
        let count = que.length
        for(let i = 0; i < count; i++){
            let node = que.shift();
            arr.push(node.val)
            if(node.left) que.push(node.left);
            if(node.right) que.push(node.right);
        }
        result.unshift(arr);
    }
    
    return result;
};
```