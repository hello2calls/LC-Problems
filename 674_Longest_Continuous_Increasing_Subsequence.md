## 674. Longest Continuous Increasing Subsequence (Easy)
Given an unsorted array of integers, find the length of longest continuous increasing subsequence (subarray).

__Example:__
```
Input: [1,3,5,4,7]
Output: 3
Explanation: The longest continuous increasing subsequence is [1,3,5], its length is 3.
Even though [1,3,5,7] is also an increasing subsequence, it's not a continuous one where 5 and 7 are separated by 4.
```
__My Solution:__
```js
var findLengthOfLCIS = function(nums) {
    let start = 0;
    let len = 0;
    for(let i=1; i<nums.length; i++){
        if(nums[i] <= nums[i-1]){
            if(i - start > len) len = i - start;
            start = i;
        }
    }
    if(nums.length - start > len) len = nums.length - start
    return len
};
```
