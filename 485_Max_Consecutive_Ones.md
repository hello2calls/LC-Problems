## 485. Max Consecutive Ones (Easy)
Given a binary array, find the maximum number of consecutive 1s in this array.

__Example 1:__
```
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
```

__ruby solution:__
```ruby
def find_max_consecutive_ones(nums)
    len = 0
    track = 0

    nums.each_index do |i|
        if nums[i] == 1
            track += 1
            len = track if track > len
        else
            track = 0
        end
    end
    len
end
```
