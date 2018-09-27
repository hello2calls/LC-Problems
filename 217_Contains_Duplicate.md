## 217. Contains Duplicate (Easy)
Given an array of integers, find if the array contains any duplicates.

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

**Example 1:**
```
Input: [1,2,3,1]
Output: true
```

__Solution:__
- sort the arr first
- return true if consecutive elements are the same.

```ruby
def contains_duplicate(nums)
    arr = nums.sort
    arr.each_index do |i|
        return true if arr[i] == arr[i+1]
    end
    false
end
```
