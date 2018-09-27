## 169. Majority Element (Easy)
Given an array of size n, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.

__Example 1:__
```
Input: [3,2,3]
Output: 3
```
**Solution:**
```ruby
def majority_element(nums)
    hsh = Hash.new(0)

    nums.each {|num| hsh[num] += 1}
    hsh.each do |k, v|
        return k if v > nums.length / 2
    end
end
```
