## 897. Increasing Order Search Tree (Easy)
Given a tree, rearrange the tree in in-order so that the leftmost node in the tree is now the root of the tree, and every node has no left child and only 1 right child.

```
Example 1:
Input: [5,3,6,2,4,null,8,1,null,null,null,7,9]

       5
      / \
    3    6
   / \    \
  2   4    8
 /        / \
1        7   9

Output: [1,null,2,null,3,null,4,null,5,null,6,null,7,null,8,null,9]

 1
  \
   2
    \
     3
      \
       4
        \
         5
          \
           6
            \
             7
              \
               8
                \
                 9  
```
__Recursion Solution:__
- use an array to store in order nodes
- calling `dfs` recursively to go left, push middle, then go right
```js
var increasingBST = function(root) {
    let arr = [];
    const dfs = (node) => {
        if(!node) return;
        dfs(node.left);
        arr.push(node);
        dfs(node.right);
    }
    dfs(root);
    for(let i=0; i < arr.length; i++){
        arr[i].left = null;
        arr[i].right = arr[i+1]
    }
    return arr[0];
};
```
__Iteration Solution:__
- need a stack array to track node order, and a result array to store node in order.
- when our stack is empty and our current node is `nil`, it means we don't have any node to push.
- we go to left first, and if we have `node.left` we push it to the stack, otherwise we pop our stack and push to the result array and go to the right side.
```ruby
def increasing_bst(root)
    stack = [root]
    result = []
    node = root.left
    until stack.empty? && node.nil?
        if node
            stack << node
            node = node.left
        else
            result << stack.pop
            node = result.last.right
        end
    end
    (0...result.length).each do |i|
        result[i].left = nil
        result[i].right = result[i+1]
    end
    result[0]
end
```
