## 867. Transpose Matrix (easy)

Given a matrix `A`, return the transpose of `A`.

The transpose of a matrix is the matrix flipped over it's main diagonal, switching the row and column indices of the matrix.

__Example:__
```
Input: [[1,2,3],[4,5,6]]
Output: [[1,4],[2,5],[3,6]]
```

__my solution__

```JavaScript
var transpose = function(A) {
    let result = [];
    for(let i = 0; i < A[0].length; i++){
        result.push([]);
    };
    for(let i = 0; i < A[0].length; i++){
        for(let j = 0; j < A.length; j++){
            result[i][j] = A[j][i];
        }
    }
    return result;
};
```

O(n*m)
