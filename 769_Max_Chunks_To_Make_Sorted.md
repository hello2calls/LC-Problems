## 769. Max Chunks To Make Sorted (Medium)
Given an array `arr` that is a permutation of `[0, 1, ..., arr.length - 1]`, we split the array into some number of "chunks" (partitions), and individually sort each chunk.  After concatenating them, the result equals the sorted array.

What is the most number of chunks we could have made?

__Example 1:__
```
Input: arr = [4,3,2,1,0]
Output: 1
Explanation:
Splitting into two or more chunks will not return the required result.
For example, splitting into [4, 3], [2, 1, 0] will result in [3, 4, 0, 1, 2], which isn't sorted.
```
__Example 2:__
```
Input: arr = [1,0,2,3,4]
Output: 4
Explanation:
We can split into two chunks, such as [1, 0], [2, 3, 4].
However, splitting into [1, 0], [2], [3], [4] is the highest number of chunks possible.
```
__Solution:__
- as we iterate through the arr, the max number we get is the max number of the current chunck. 
- so if the max number is equal to the current index, it means we can close the chunck at that point. 
```js
var maxChunksToSorted = function(arr) {
    let count = 0;
    let max = 0;
    for(let i = 0; i<arr.length; i++){
        max = Math.max(max, arr[i]);
        if(max === i) count++;
    }
    return count;
};
```