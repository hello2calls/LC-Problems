## 219. Contains Duplicate II (Easy)
Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that **nums[i] = nums[j]** and the **absolute** difference between i and j is at most k.

__Example 1:__
```
Input: nums = [1,2,3,1], k = 3
Output: true
```
__Example 2:__
```
Input: nums = [1,2,3,1,2,3], k = 2
Output: false
```
__My Solution:__
- use hash to store the index.
- iterate through the `nums` array, if we already have the `el`in our hash, that means that we met the same element in the array, so we can check if the current index - the index in our hash is at most K, if it is within the `k`, we return true, otherwise we update our index to the current index in our hash.
```ruby
def contains_nearby_duplicate(nums, k)
    hsh = Hash.new
    nums.each_with_index do |el, i|
        if hsh[el]
            return true if (i - hsh[el]).abs <= k
            hsh[el] = i
        else
            hsh[el] = i
        end
    end
    false
end
```
