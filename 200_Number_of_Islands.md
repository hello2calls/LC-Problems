## 200. Number of Islands (Medium)
  Given a 2d grid map of `'1'`s (land) and `'0'`s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

  __Example 1:__
  ```
  Input:
11000
11000
00100
00011

Output: 3
  ```
  **My Solution:**
  - iterate through each square. if the square is "1", increment the sum. and then call helper func to update the grid
  - the helper func will change all square "1" to "0".
  ```ruby
def num_islands(grid)
    sum = 0
    grid.each_with_index do |row, r|
        row.each_index do |c|
            if grid[r][c] == '1'
                sum += 1
                grid = helper(r, c, grid)
            end
        end
    end
    sum
end

def helper(r, c, grid)
    if r < 0 || r >= grid.length || grid[r][c] == '0' || c < 0 || c >= grid[0].length
        return
    end
    grid[r][c] = '0'
    helper(r-1, c, grid)
    helper(r+1, c, grid)
    helper(r, c-1, grid)
    helper(r, c+1, grid)
    grid
end
```
