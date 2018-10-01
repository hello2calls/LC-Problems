## 643. Maximum Average Subarray I (Easy)
Given an array consisting of `n` integers, find the contiguous subarray of given length `k` that has the maximum average value. And you need to output the maximum average value.

__Example 1:__
```
Input: [1,12,-5,-6,50,3], k = 4
Output: 12.75
Explanation: Maximum average is (12-5-6+50)/4 = 51/4 = 12.75
```

__solution:__
```ruby
def find_max_average(nums, k)
    start = 0
    sum = 0
    (0...k).each {|i| sum += nums[i]}
    max = sum
    (k...nums.length).each do |i|
        sum = sum - nums[start] + nums[i]
        max = [sum, max].max
        start += 1
    end
    max.to_f / k
end
```
