## 62. Unique Paths (Medium)
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?
![](https://assets.leetcode.com/uploads/2018/10/22/robot_maze.png)
Above is a 7 x 3 grid. How many possible unique paths are there?

__Example 1:__
```
Input: m = 3, n = 2
Output: 3
Explanation:
From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Right -> Down
2. Right -> Down -> Right
3. Down -> Right -> Right
```

__My Solution:__
- using DP
- from `grid[0][0]` to `grid[0][1]` only has one path; from `grid[0][0]` to `grid[0][1]` only has one path. So we know from `grid[0][0]` to `grid[1][1]` has two paths, which are "right -> down" and "down -> right"
- the number of path of getting into current position `[r][c]` is the sum of the path to `[r-1][c]`(top) and the path to `[r][c-1]`(left)
```js
var uniquePaths = function(m, n) {
    let grid = [];
    for(let r=0; r<n; r++){
        grid.push([]);
        for(let c=0; c<m; c++){
            if (r === 0 && c === 0){
                grid[0][0] = 1;
                continue;
            }
            if(r-1 >= 0 && c-1 >= 0){
                grid[r][c] = grid[r][c-1] + grid[r-1][c];
            }else if(r-1 >= 0){
                grid[r][c] = grid[r-1][c];
            }else if(c-1 >= 0){
                grid[r][c] = grid[r][c-1];
            } 
        }
    }
    return grid[n-1][m-1]
};
```