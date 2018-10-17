## 238. Product of Array Except Self (Medium)
Given an array `nums` of n integers where n > 1,  return an array `output` such that `output[i]` is equal to the product of all the elements of `nums` except `nums[i]`

__Example:__
```
Input:  [1,2,3,4]
Output: [24,12,8,6]
```
**Note**: Please solve it without division and in O(n).

**Follow up**:
Could you solve it with constant space complexity? (The output array **does not** count as extra space for the purpose of space complexity analysis.)

__My Solution:__
- iterate from left to right to calculate the product of all left side elements of current index
- iterate from right to left to calculate the right side
- adding them together
```js
var productExceptSelf = function(nums) {
    let result = [];
    for(let i=0; i<nums.length; i++){
        if(i === 0){
            result[i] = 1;
            continue;
        }
        result.push(nums[i-1] * result[i-1])
    }
    let n = 1;
    for(let i = nums.length-1; i>=0; i--){
        if(i === nums.length-1) continue;
        n *= nums[i+1];
        result[i] = result[i] * n
    }
    return result;
};
```
