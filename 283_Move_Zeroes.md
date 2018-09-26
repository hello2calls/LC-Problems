## 283. Move Zeroes (Easy)
Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

__Example:__
```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```
__My Ruby Solution:__
```ruby
def move_zeroes(nums)
    idx = 0
    nums.each_index do |i|
        if nums[i] != 0
            nums[idx], nums[i] = nums[i], nums[idx]
            idx += 1
        end
    end
    nums
end
```
- idx as a pointer, elements before `idx` are non-zero element.
