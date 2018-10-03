## 653. Two Sum IV - Input is a BST (Easy)
Given a Binary Search Tree and a target number, return true if there exist two elements in the BST such that their sum is equal to the given target.

__Example 1:__
```
Input:
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

Output: True
```

__Solution1:__
- using hash
```js
var findTarget = function(root, k) {

    const find = (node, k, hash = {}) => {
        if(!node) return false;
        if(hash[k - node.val]) return true;
        hash[node.val] = true;

        return find(node.left, k, hash) || find(node.right, k, hash);
    }

    return find(root, k);
};
```
__Solution2:__
- using BFS and hash
```js
var findTarget = function(root, k) {
    let hsh = {};
    let queue = [root]
    while(queue.length > 0){
        node = queue.shift()
        if(hsh[k - node.val]){
            return true;
        }else{
            hsh[node.val] = true;
        }
        if(node.left) queue.push(node.left);
        if(node.right) queue.push(node.right);
    }

    return false;
};
```
Complexity Analysis

- Time complexity : O(n). The entire tree is traversed only once in the worst case. Here, n refers to the number of nodes in the given tree.

- Space complexity : O(n). The size of the setset can grow upto n in the worst case.
