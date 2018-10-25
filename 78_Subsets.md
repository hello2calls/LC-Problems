## 78. Subsets (Medium)
Given a set of distinct integers, nums, return all possible subsets (the power set).

**Note**: The solution set must not contain duplicate subsets.

__Example:__
```
Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```

__Back Tracking Solution:__

```js
var subsets = function(nums) {
    const helper = (temp, res, i) => {
        res.push([...temp]);
        if(i < nums.length){
            for(let j=i; j<nums.length;j++){
                temp.push(nums[j]);
                helper(temp, res, j+1)
                temp.pop();
            }
        }
        return res;
    }
    return helper([], [], 0)
};
```