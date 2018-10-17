## 442. Find All Duplicates in an Array (Medium)
Given an array of integers, 1 ≤ a[i] ≤ n (n = size of array), some elements appear **twice** and others appear **once**.

Find all the elements that appear **twice** in this array.

Could you do it without extra space and in O(n) runtime?

__Example:__
```
Input:
[4,3,2,7,8,2,3,1]

Output:
[2,3]
```
__My Solution:__
- iterate throught the nums array, set the nums[nums[i] - 1] to negative value.
- when we meet the same number again, the value of that index is negative, so we can push it into our result array.
```js
var findDuplicates = function(nums) {
    let result = [];
    for(let i = 0; i < nums.length; i++){
        if(nums[Math.abs(nums[i]) - 1] < 0) result.push(Math.abs(nums[i]));
        nums[Math.abs(nums[i]) - 1] = - nums[Math.abs(nums[i]) - 1]
    }

    return result;
};
```
