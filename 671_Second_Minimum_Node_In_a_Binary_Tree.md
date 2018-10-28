## 671. Second Minimum Node In a Binary Tree (Easy)
Given a non-empty special binary tree consisting of nodes with the non-negative value, where each node in this tree has exactly **two** or **zero** sub-node. **If the node has two sub-nodes, then this node's value is the smaller value among its two sub-nodes.**

Given such a binary tree, you need to output the **second minimum** value in the set made of all the nodes' value in the whole tree.

If no such second minimum value exists, output -1 instead.

__Example 1:__
```
Input: 
    2
   / \
  2   5
     / \
    5   7

Output: 5
Explanation: The smallest value is 2, the second smallest value is 5.
```
__Example 2:__
```
Input: 
    2
   / \
  2   2

Output: -1
Explanation: The smallest value is 2, but there isn't any second smallest value.
```
__My Solution:__
- So we know the root node is the smallest value in the tree. If current node's value is equal to the root node value, we can directly return current node's value because we know it is the smallest value in its sub-tree. 
- When current node value is equal to the root node value, we need to traverse its children and get the minimum value from its left sub-tree and right sub-tree.
```js
var findSecondMinimumValue = function(root) {
    if (!root) return -1;
    let min = root.val;
    const traverse = (node) => {
        if (!node) return +Infinity;
        if (node.val === min) {
            return Math.min(traverse(node.left), traverse(node.right));
        }
        return node.val;
    }
    let res = Math.min(traverse(root.left), traverse(root.right));
    return res === Infinity ? -1 : res;
};
```