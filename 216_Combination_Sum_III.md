## 216. Combination Sum III (Medium)
Find all possible combinations of **k** numbers that add up to a number n, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.

__Example 1:__
```
Input: k = 3, n = 7
Output: [[1,2,4]]
```
__Example 2:__
```
Input: k = 3, n = 9
Output: [[1,2,6], [1,3,5], [2,3,4]]
```
__Solution:__
- use backtrack or dfs
```js
const helper = (s, cur, start, n, res, k) => {
    if (s === n && cur.length === k) {
        res.push([...cur]);
    } else if (s < n) { 
        for (let i = start; i <= 9; i++) {
            if (s + i <= n && cur.length+1 <= k) {
                cur.push(i);
                helper(s+i, cur, i+1, n, res, k);
                cur.pop();
            }
        }
    }
    return res;
};

var combinationSum3 = function(k, n) {
    
    return helper(0, [], 1, n, [], k);
};
```