## 404. Sum of Left Leaves (Easy)
Find the sum of all left leaves in a given binary tree.

__Example:__
```
      3
     / \
    5  20
   /  /  \
  9  15   7

There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.
```
__My Solution:__  
```js
var sumOfLeftLeaves = function(root) {
    if(!root) return 0;
    let sum = 0;
    const traverse = (node) => {
        if(!node) return;
        if(node.left && !(node.left.left || node.left.right)){
            sum += node.left.val
        }
        traverse(node.left);
        traverse(node.right);
        
    }
    traverse(root)
    return sum;
};
```