## 108. Convert Sorted Array to Binary Search Tree (Easy)
Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

__Example:__
```
Given the sorted array: [-10,-3,0,5,9],

One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:

      0
     / \
   -3   9
   /   /
 -10  5
```
__My Solution:__
```ruby
def sorted_array_to_bst(nums)
    return nil if nums.empty?
    idx = nums.length / 2
    node = TreeNode.new(nums[idx])
    node.left = sorted_array_to_bst(nums[0...idx])
    node.right = sorted_array_to_bst(nums[idx+1..-1])
    node
end
```
Time: O(logn)
Space: O(logn) (call stack)