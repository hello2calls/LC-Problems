## 669. Trim a Binary Search Tree (Easy)
Given a binary search tree and the lowest and highest boundaries as `L` and `R`, trim the tree so that all its elements lies in `[L, R]` (R >= L). You might need to change the root of the tree, so the result should return the new root of the trimmed binary search tree.

__Example 1:__
```
Input:
    1
   / \
  0   2

  L = 1
  R = 2

Output:
    1
      \
       2
```
__Example 2:__
```
Input:
    3
   / \
  0   4
   \
    2
   /
  1

  L = 1
  R = 3

Output:
      3
     /
   2   
  /
 1
```
__My Solution:__
- if the root is in the range `[L, R]`, we trim its left and right side.
- if the root is less than `L`, it means that only its right side has the possibility to be returned, so we only need to trim its right side.
- if the root is greater than `R`, it means that only its left side has the possibility to be returned, so we only need to trim its left side.
```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @param {number} L
 * @param {number} R
 * @return {TreeNode}
 */
var trimBST = function(root, L, R) {
    if(!root) return [];
    const trim = (node) => {
        if(!node) return null;
        if(node.val >= L && node.val <= R){
            node.left = trim(node.left);
            node.right = trim(node.right);
            return node;
        }else if(node.val < L){
            return trim(node.right);
        }else if(node.val > R){
            return trim(node.left);
        }
    }
    return trim(root);
};
```
**Complexity Analysis**

- Time Complexity: O(N), where NN is the total number of nodes in the given tree. We visit each node at most once.

- Space Complexity: O(N). Even though we don't explicitly use any additional memory, the call stack of our recursion could be as large as the number of nodes in the worst case.
