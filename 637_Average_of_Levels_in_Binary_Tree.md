## 637. Average of Levels in Binary Tree (Easy)
Given a non-empty binary tree, return the average value of the nodes on each level in the form of an array.

__Example 1:__
```
Input:
    3
   / \
  9  20
    /  \
   15   7
Output: [3, 14.5, 11]
Explanation:
The average value of nodes on level 0 is 3,  on level 1 is 14.5, and on level 2 is 11. Hence return [3, 14.5, 11].
```

__my solution:__
- BFS iteration
- use `arr[i]` to store sum of nodes' values at `i`th level
- `nodes` array stores current level's nodes
- in the `while` loop, the `children` array stores all children of current level's nodes. If `children` array is empty, that means current level's nodes have no more children, then we can break our `while` loop
```ruby
# Definition for a binary tree node.
# class TreeNode
#     attr_accessor :val, :left, :right
#     def initialize(val)
#         @val = val
#         @left, @right = nil, nil
#     end
# end

# @param {TreeNode} root
# @return {Float[]}
def average_of_levels(root)
    arr = [[root.val]]
    nodes = [root]
    while true
        children = []
        nodes.each do |node|
            children << node.left if node.left
            children << node.right if node.right
        end
        if children.empty?
            break
        else
            arr << children.map {|n| n.val}
            nodes = children
        end
    end
    arr.map do |nodes|
        (nodes.reduce(:+)).to_f / nodes.length
    end
end
```
__DFS JS Solution:__
- use two arrays `res` and `count`. Here `res[i]` refers to the sum at `i`th level, `count[i]` refers to the number of nodes at `i`th level.
- We make use of a function `average(t, i, res, count)`, which is used to fill the `res` and `count` array if we start the DFS from the node `t` at the `i`th level in the given tree. We start by making the function call `average(root, 0, res, count)`. After this, we do the following at every step:

    1. Add the value of the current node to the resres(or sumsum) at the index corresponding to the current level. Also, increment the countcount at the index corresponding to the current level.

    2. Call the same function, average, with the left and the right child of the current node. Also, update the current level used in making the function call.

    3. Repeat the above steps till all the nodes in the given tree have been considered once.

    4. Populate the averages in the resultant array to be returned.
```js
var averageOfLevels = function(root) {
    const average = (node, level, sumArr, countArr) => {
        if(!node) return;
        if(level < sumArr.length){
            sumArr[level] += node.val;
            countArr[level]++;
        }else{
            sumArr[level] = node.val;
            countArr[level] = 1;
        }
        average(node.left, level+1, sumArr, countArr);
        average(node.right, level+1, sumArr, countArr);
    }
    let res = [];
    let count = [];
    average(root, 0, res, count);
    return res.map((sum, i) => sum / count[i]);

};
```
**Complexity Analysis**

- Time complexity : O(n). The whole tree is traversed once only. Here, nn refers to the total number of nodes in the given binary tree.

- Space complexity : O(h). resres and countcount array of size hh are used. Here, hh refers to the height(maximum number of levels) of the given binary tree. Further, the depth of the recursive tree could go upto hh only.
