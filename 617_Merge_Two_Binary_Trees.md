## 617. Merge Two Binary Trees (Easy)
Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.

You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.

__Example 1:__
```
Example 1:

Input:
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  
Output:
Merged tree:
	     3
	    / \
	   4   5
	  / \   \
	 5   4   7
```

__My solution:__
- base case: if tree1 and tree2 both are null, return empty array.
- if two tree both exist, make a new tree node with the sum of their values, and assign `left` and `right` calling the merge recursively to the new node.
```js
var mergeTrees = function(t1, t2) {
    if(!t1 && !t2) return [];
    const merge = (n1, n2) => {
        let val;
        let node;
        if(n1 && n2){
            val = n1.val + n2.val;
            node = new TreeNode(val);
            node.left = merge(n1.left, n2.left);
            node.right = merge(n1.right, n2.right);
            return node;
        }else if(n1){
            return n1;
        }else if(n2){
            return n2
        }else {
            return null;
        }
    }
    return merge(t1, t2);
};
```
