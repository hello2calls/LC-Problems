## 628. Maximum Product of Three Numbers (Easy)
Given an integer array, find three numbers whose product is maximum and output the maximum product.

__Example:__
```
Input: [1,2,3,4]
Output: 24
```

__Solution:__
- we will have two situations:
    1. there are 3 or more than 3 positive numbers or all negative numbers
    2. there is only one positive number with other negative numbers
- so after the array sorted, the max product will either be the product of last three numbers or the product of first two number with last number.

```ruby
def maximum_product(nums)
    nums = nums.sort
    p1 = nums[-3] * nums[-2] * nums[-1]
    p2 = nums[0] * nums[1] * nums[-1]
    [p1, p2].max
end
```
