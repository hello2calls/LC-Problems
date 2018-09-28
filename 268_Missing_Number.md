## 268. Missing Number (Easy)
Given an array containing n distinct numbers taken from `0, 1, 2, ..., n`, find the one that is missing from the array.

__Example:__
```
Input: [9,6,4,2,3,5,7,0,1]
Output: 8
```
__Solution:__
- since there is only one number is missing, we can simply using the sum of 0 to n, minus the sum of nums array to find the missing number
```ruby
def missing_number(nums)
    total = (0..nums.length).to_a.reduce(:+)
    sum = nums.reduce(:+)
    total - sum
end
```
