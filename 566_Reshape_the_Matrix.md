## 566. Reshape the Matrix (Easy)
You're given a matrix represented by a two-dimensional array, and two positive integers r and c representing the row number and column number of the wanted reshaped matrix, respectively.

The reshaped matrix need to be filled with all the elements of the original matrix in the same row-traversing order as they were.

If the 'reshape' operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.

__Example 1:__
```
nums =
[[1,2],
 [3,4]]
r = 1, c = 4
Output:
[[1,2,3,4]]
Explanation:
The row-traversing of nums is [1,2,3,4]. The new reshaped matrix is a 1 * 4 matrix, fill it row by row by using the previous list.
```
__my ruby solution:__
```ruby
def matrix_reshape(nums, r, c)
    return nums if (r * c) != (nums.length * nums[0].length)
    result = Array.new(r) {Array.new}
    track = c
    row = 0
    nums.each do |arr|
        arr.each do |el|
            result[row] << el
            track -= 1
            if track == 0
                track = c
                row += 1
            end
        end
    end
    result
end
```

start from the first row in result arr, each time after push 1 elment, decrement the track by 1, if the track is 0, change to the next row in result array.

__complexity__
O(n*m)
