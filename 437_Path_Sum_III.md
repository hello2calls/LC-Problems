## 437. Path Sum III (Easy)
You are given a binary tree in which each node contains an integer value.

Find the number of paths that sum to a given value.

The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).

The tree has no more than 1,000 nodes and the values are in the range -1,000,000 to 1,000,000.

__Example:__
```
root = [10,5,-3,3,2,null,11,3,-2,null,1], sum = 8

      10
     /  \
    5   -3
   / \    \
  3   2   11
 / \   \
3  -2   1

Return 3. The paths that sum to 8 are:

1.  5 -> 3
2.  5 -> 2 -> 1
3. -3 -> 11
```
__Solution:__
```js
var pathSum = function(root, sum) {
    if(!root) return 0;
    const track = (node, cur) => {
        if(!node) return 0;
        if(cur + node.val === sum){
            return 1 + track(node.left, cur+node.val) + track(node.right, cur+node.val);
        }
        if(sum !== cur && !node.left && !node.right) return 0; 
        return track(node.left, cur+node.val) + track(node.right, cur+node.val);
    }
    
    return track(root, 0) + pathSum(root.left, sum) + pathSum(root.right, sum)
    
};
```