## 448. Find All Numbers Disappeared in an Array(Easy)

Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements of [1, n] inclusive that do not appear in this array.

Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

__Example:__
```
Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
```
__solution__
- useing index as reference for the number. if the number is in the `nums`, change the number index to negative.
- in next iteration, if the element is not negative, push the index + 1 to the result array

```ruby
def find_disappeared_numbers(nums)
    result = []
    nums.each do |n|
        if nums[n.abs - 1] > 0
            nums[n.abs - 1] = -nums[n.abs - 1]
        end
    end
    nums.each_index do |i|
        result << i + 1 if nums[i] > 0
    end
    result
end
```
