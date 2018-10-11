## 840. Magic Squares In Grid (Easy)
A 3 x 3 magic square is a 3 x 3 grid filled with distinct numbers **from 1 to 9** such that each row, column, and both diagonals all have the same sum.

Given an `grid` of integers, how many 3 x 3 "magic square" subgrids are there?  (Each subgrid is contiguous).

__Example 1:__
```
Input: [[4,3,8,4],
        [9,5,1,9],
        [2,7,6,2]]
Output: 1
Explanation:
The following subgrid is a 3 x 3 magic square:
438
951
276

while this one is not:
384
519
762

In total, there is only one magic square inside the given grid.
```
__Solution:__
- The sum of the grid must be 45, as it is the sum of the distinct values from 1 to 9.
- Each horizontal and vertical line must add up to 15, as the sum of 3 of these lines equals the sum of the whole grid.
```ruby
def num_magic_squares_inside(grid)
    sum = 0
    (0..grid.length-3).each do |r|
        (0..grid[0].length-3).each do |c|
            sum += 1 if helper(r, c, grid)
        end
    end
    sum
end

def helper(r, c, grid)
    hsh = Hash.new(0)
    (r..r+2).each do |i|
        (c..c+2).each do |j|
            hsh[grid[i][j]] += 1
        end
    end
    (1..9).each do |n|
        return false if hsh[n] != 1
    end
    return (grid[r][c] + grid[r][c+1] + grid[r][c+2] == 15 &&
            grid[r+1][c] + grid[r+1][c+1] + grid[r+1][c+2] == 15 &&
            grid[r+2][c] + grid[r+2][c+1] + grid[r+2][c+2] == 15 &&
            grid[r][c] + grid[r+1][c] + grid[r+2][c] == 15 &&
            grid[r][c+1] + grid[r+1][c+1] + grid[r+2][c+1] == 15 &&
            grid[r][c+2] + grid[r+1][c+2] + grid[r+2][c+2] == 15 &&
            grid[r][c] + grid[r+1][c+1] + grid[r+2][c+2] == 15 &&
            grid[r][c+2] + grid[r+1][c+1] + grid[r+2][c] == 15
        )

end
```
