## 414. Third Maximum Number (Easy)
Given a **non-empty** array of integers, return the **third** maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).

__Example 1:__
```
Input: [3, 2, 1]

Output: 1

Explanation: The third maximum is 1.
```
__Example 2:__
```
Input: [1, 2]

Output: 2

Explanation: The third maximum does not exist, so the maximum (2) is returned instead.
```
__My Solution:__

```ruby
def third_max(nums)
    one = nums[0]
    two = nil
    three = nil

    (1...nums.length).each do |i|
        next if [one, two, three].include?(nums[i])
        if nums[i] > one
            three = two
            two = one
            one = nums[i]
        elsif two.nil? || nums[i] > two
            three = two
            two = nums[i]
        elsif three.nil? || nums[i] > three
            three = nums[i]
        end
    end
    return three if three
    one
end
```
