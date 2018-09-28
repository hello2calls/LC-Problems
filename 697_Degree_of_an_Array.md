## 697. Degree of an Array (Easy)
Given a non-empty array of non-negative integers `nums`, the **degree** of this array is defined as the maximum frequency of any one of its elements.

Your task is to find the smallest possible length of a (contiguous) subarray of `nums`, that has the same degree as `nums`.

__Example 1:__
```
Input: [1, 2, 2, 3, 1]
Output: 2
Explanation:
The input array has a degree of 2 because both elements 1 and 2 appear twice.
Of the subarrays that have the same degree:
[1, 2, 2, 3, 1], [1, 2, 2, 3], [2, 2, 3, 1], [1, 2, 2], [2, 2, 3], [2, 2]
The shortest length is 2. So return 2.
```
__Solution:__
1. make an empty hash, variable `freq` to track max frequency, variable `len` to track min length of max frequency.
2. in the hash, the key is the number, the value is an array in which first element is starting index of the number, second element is the frequency of that number.
3. if the hash does not have the key of the number, I initiallize `hsh[number] = [i, 1]`
4. if the hash has the number already:
    - increment the frequency in the hash
    - compare the frequency of the number with the max frequency
    - if it is greater than the max, update the max and update the min length
    - if it is equal to the max, we compare the length with min length, and take the smaller one.


```ruby
def find_shortest_sub_array(nums)
    hsh = Hash.new
    freq = 1
    len = 1
    nums.each_with_index do |k, i|
        if !hsh[k]
            hsh[k] = [i, 1]
        else
            hsh[k][1] += 1
            if hsh[k][1] > freq
                freq = hsh[k][1]
                len = i + 1 - hsh[k][0]
            elsif hsh[k][1] == freq
                len = [len, i + 1 - hsh[k][0]].min
            end
        end
    end
    len

end
```
