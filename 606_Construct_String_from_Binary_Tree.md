## 606. Construct String from Binary Tree (Easy)
You need to construct a string consists of parenthesis and integers from a binary tree with the preorder traversing way.

The null node needs to be represented by empty parenthesis pair "()". And you need to omit all the empty parenthesis pairs that don't affect the one-to-one mapping relationship between the string and the original binary tree.

__Example 1:__
```
Input: Binary tree: [1,2,3,4]
       1
     /   \
    2     3
   /    
  4     

Output: "1(2(4))(3)"

Explanation: Originallay it needs to be "1(2(4)())(3()())",
but you need to omit all the unnecessary empty parenthesis pairs.
And it will be "1(2(4))(3)".
```
__Example 2:__
```
Input: Binary tree: [1,2,3,null,4]
       1
     /   \
    2     3
     \  
      4

Output: "1(2()(4))(3)"

Explanation: Almost the same as the first example,
except we can't omit the first parenthesis pair to break the one-to-one mapping relationship between the input and the output.
```

__My Solution:__
```ruby
def tree2str(t)
    return "" if t.nil?
    return t.val.to_s if t.left.nil? && t.right.nil?
    left = tree2str(t.left)
    right = tree2str(t.right)
    if right == ""
        return "#{t.val}(#{left})"
    else
        return "#{t.val}(#{left})(#{right})"
    end
end
```

Complexity Analysis

- Time complexity : O(n). The preorder traversal is done over the nn nodes of the given Binary Tree.

- Space complexity : O(n). The depth of the recursion tree can go upto n in case of a skewed tree.
