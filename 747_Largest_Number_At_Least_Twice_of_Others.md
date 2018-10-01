## 747. Largest Number At Least Twice of Others (Easy)
In a given integer array `nums`, there is always exactly one largest element.

Find whether the largest element in the array is at least twice as much as every other number in the array.

If it is, return the index of the largest element, otherwise return -1.

__Examples:__
```
Input: nums = [3, 6, 1, 0]
Output: 1
Explanation: 6 is the largest integer, and for every other number in the array x,
6 is more than twice as big as x.  The index of value 6 is 1, so we return 1.

Input: nums = [1, 2, 3, 4]
Output: -1
Explanation: 4 isn't at least as big as twice the value of 3, so we return -1.
```
__My Solution:__
- `max` variable tracking the max number in the array
- `idx` variable tracking valid result index.
- iterate through `nums`, if current num is greater than max. update the max, and update the valid index if current num is greater than `max * 2`, otherwise, set the idx to "-1".

```js
var dominantIndex = function(nums) {
    if(nums.length < 2) return 0;
    let max = nums[0];
    let idx = 0;
    for(let i=1; i<nums.length; i++){
        if(nums[i] > max){
            if(nums[i] >= max * 2){
                max = nums[i];
                idx = i;
            }else{
                max = nums[i];
                idx = -1;
            }
        }else if(max < nums[i]*2){
            idx = -1;
        }
    }
    return idx;
};
```
