## 695. Max Area of Island (Easy)
Given a non-empty 2D array `grid` of 0's and 1's, an island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.

Find the maximum area of an island in the given 2D array. (If there is no island, the maximum area is 0.)

__Example 1:__
```
[[0,0,1,0,0,0,0,1,0,0,0,0,0],
 [0,0,0,0,0,0,0,1,1,1,0,0,0],
 [0,1,1,0,1,0,0,0,0,0,0,0,0],
 [0,1,0,0,1,1,0,0,1,0,1,0,0],
 [0,1,0,0,1,1,0,0,1,1,1,0,0],
 [0,0,0,0,0,0,0,0,0,0,1,0,0],
 [0,0,0,0,0,0,0,1,1,1,0,0,0],
 [0,0,0,0,0,0,0,1,1,0,0,0,0]]
```
Given the above grid, return 6. Note the answer is not 11, because the island must be connected 4-directionally.

__solution:__
- iterate through every square, and call `dfs` on each spuare to find the sum of the lands starting at that square.
- in `dfs`, if `grid[r][c]` is not 0, and is in the grid, and have not been seen, return 1 amount of land + other direction sum.
```ruby
def max_area_of_island(grid)
    seen = Array.new(grid.length) {Array.new(grid[0].length,false)}
    sum = 0
    grid.each_with_index do |row, r|
        row.each_with_index do |col, c|
            sum = [sum, dfs(r, c, grid, seen)].max
        end
    end
    sum
end

def dfs(r, c, grid, seen)
    if (r < 0) || (r >= seen.length) || (c < 0) || (c >= seen[0].length) || (grid[r][c] == 0) || (seen[r][c])
        return 0
    else
        seen[r][c] = true
        return 1 + dfs(r+1, c, grid, seen) + dfs(r-1, c, grid, seen) + dfs(r, c+1, grid, seen) + dfs(r, c-1, grid, seen)
    end
end
```

__Complexity Analysis__
- Time Complexity: O(R∗C), where R is the number of rows in the given grid, and C is the number of columns. We visit every square once.
- Space complexity: O(R*C), the space used by seen to keep track of visited squares, and the space used by stack.
