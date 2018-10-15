## 581. Shortest Unsorted Continuous Subarray (Easy)
Given an integer array, you need to find one **continuous subarray** that if you only sort this subarray in ascending order, then the whole array will be sorted in ascending order, too.

You need to find the shortest such **subarray** and output its length.

__Example 1:__
```
Input: [2, 6, 4, 8, 10, 9, 15]
Output: 5
Explanation: You need to sort [6, 4, 8, 10, 9] in ascending order to make the whole array sorted in ascending order.
```
__Solution:__
- first, find the position where the sort goes wrong. Left: when the `nums[i+1] < nums[i]`. Right: when the `nums[j] < nums[j-1]`
- then, find the minimun and maximun in `nums[i..j]`
- find the right position for the `min` and `max`
- return the length between the positions of `min` and `max`
![](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/Figures/581/Unsorted_subarray_2.PNG)

```ruby
def find_unsorted_subarray(nums)
    i = 0
    j = nums.length - 1

    while i < j
        if nums[i] <= nums[i+1] && nums[j] >= nums[j-1]
            i += 1
            j -= 1

        elsif nums[i] <= nums[i+1]
            i += 1
        elsif nums[j] >= nums[j-1]
            j -= 1
        else
            break
        end
    end
    return 0 if i >= j
    min = nums[i..j].min
    max = nums[i..j].max
    l_idx = i
    (0..i).each do |idx|
        if nums[idx] > min
            l_idx = idx
            break
        end
    end
    r_idx = j
    (-nums.length+1..-j).each do |idx|
        if nums[-idx] < max
            r_idx = -idx
            break
        end
    end

    r_idx - l_idx + 1
end
```
