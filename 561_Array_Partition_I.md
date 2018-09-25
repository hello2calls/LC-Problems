## 561. Array Partition I (easy)

Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

__Example 1:__
```
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).
```
__my solution:__
1. sort the array fisrt
2. the largest num we can add to the sum is the second to last number, then keep subtracting 2.
3. the last number we can add will be the first element or the second element, therefore the while loop condition is `while i > 1`
```JavaScript
var arrayPairSum = function(nums) {
    nums = nums.sort((a,b) => a-b);
    let i = nums.length - 2;
    let sum = nums[i];
    while(i > 1){
        i -= 2;
        sum += nums[i];
    }
    return sum;
};
```

__complexity:__
Since I need to sort the array, the Time Complexity is O(logn) or O(nlogn) based on the js built in sort, Space O(1)
