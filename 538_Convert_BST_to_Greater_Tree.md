## 538. Convert BST to Greater Tree (Easy)
Given a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus sum of all keys greater than the original key in BST.

__Example:__
```
Input: The root of a Binary Search Tree like this:
              5
            /   \
           2     13

Output: The root of a Greater Tree like this:
             18
            /   \
          20     13
```

__My Solution:__
- it is reverse in-order: right -> middle -> left
- starting from the very right node of the tree, because it is the largest node in the tree. make a `sum` variable to track the biggest current sum.
- reset the node value to current sum
```js
var convertBST = function(root) {
    if(!root) return [];
    let sum = 0;
    const convert = (node) => {
        if(!node) return 0;
        convert(node.right);
        sum += node.val;
        node.val = sum;
        convert(node.left);
    }
    convert(root);
    return root;
};
```

Complexity Analysis

- Time complexity : O(n)

  A binary tree has no cycles by definition, so `convert` gets called on each node no more than once. Other than the recursive calls, `convert` does a constant amount of work, so a linear number of calls to `convert` will run in linear time.

- Space complexity : O(n)

  Using the prior assertion that `convert` is called a linear number of times, we can also show that the entire algorithm has linear space complexity. Consider the worst case, a tree with only right (or only left) subtrees. The call stack will grow until the end of the longest path is reached, which in this case includes all nn nodes.
