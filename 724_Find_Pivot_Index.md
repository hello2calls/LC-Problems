## 724. Find Pivot Index (Easy)
Given an array of integers `nums`, write a method that returns the "pivot" index of this array.

We define the pivot index as the index where the sum of the numbers to the left of the index is equal to the sum of the numbers to the right of the index.

If no such index exists, we should return -1. If there are multiple pivot indexes, you should return the left-most pivot index.

__Example:__
```
Input:
nums = [1, 7, 3, 6, 5, 6]
Output: 3
Explanation:
The sum of the numbers to the left of index 3 (nums[3] = 6) is equal to the sum of numbers to the right of index 3.
Also, 3 is the first index where this occurs.
```
__Solution:__
- start from index 0
- left sum start at 0, right sum is equal to total sum minus left sum minus current number.
```ruby
def pivot_index(nums)
    left = 0
    sum = nums.reduce(:+)
    nums.each_index do |i|
        return i if left == sum - left - nums[i]
        left += nums[i]
    end
    -1
end
```
