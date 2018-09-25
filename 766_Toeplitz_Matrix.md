## 766. Toeplitz Matrix (Easy)

A matrix is Toeplitz if every diagonal from top-left to bottom-right has the same element.

Now given an `M x N` matrix, return `True` if and only if the matrix is Toeplitz.


__Example 1:__
```
Input:
matrix = [
  [1,2,3,4],
  [5,1,2,3],
  [9,5,1,2]
]
Output: True
Explanation:
In the above grid, the diagonals are:
"[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", "[4]".
In each diagonal all elements are the same, so the answer is True.
```

__JS solution__
```JavaScript
var isToeplitzMatrix = function(matrix) {
    let str1, str2;
    for(let i = 0; i < matrix.length - 1; i++){
        str1 = matrix[i].slice(0, matrix[i].length - 1).join("");
        str2 = matrix[i+1].slice(1).join("");
        if(str1 !== str2){
            return false;
        }
    }
    return true;
};
```
__ruby solution__
```ruby
def is_toeplitz_matrix(matrix)
    (0...matrix.length - 1).each do |i|
        return false if matrix[i][0..-2] != matrix[i+1][1..-1]
    end
    true
end
```

each time I only need to compare elements in the current row `matrix[i]` with next row `matrix[i+!]`. If the diagonal is the same, `current_row[0..-2]` will be the same with `next_row[1..-1]`.
