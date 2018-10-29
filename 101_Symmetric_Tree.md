## 101. Symmetric Tree (Easy)
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:
```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```
But the following `[1,2,2,null,3,null,3]` is not:
```
    1
   / \
  2   2
   \   \
   3    3
```

__Solution:__
Two trees are a mirror reflection of each other if:

1. Their two roots have the same value.
2. The right subtree of each tree is a mirror reflection of the left subtree of the other tree.
![](https://leetcode.com/media/original_images/101_Symmetric_Mirror.png)

```js
var isSymmetric = function(root) {
    if (!root) return true;
    
    const helper = (n1, n2) => {
        if (!n1 && !n2) return true;
        if (!n1 || !n2) return false;
        if (n1.val === n2.val) {
            let left = helper(n1.left, n2.right);
            let right = helper(n1.right, n2.left);
            return left && right;
        }
        return false;
    }
    return helper(root, root);
};
```
Complexity Analysis

Time complexity : O(n). Because we traverse the entire input tree once, the total run time is O(n), where n is the total number of nodes in the tree.

Space complexity : The number of recursive calls is bound by the height of the tree. In the worst case, the tree is linear and the height is in O(n). Therefore, space complexity due to recursive calls on the stack is O(n) in the worst case. 
