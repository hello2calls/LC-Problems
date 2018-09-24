## 832. Flipping an Image (Easy)

Given a binary matrix `A`, we want to flip the image horizontally, then invert it, and return the resulting image.

To flip an image horizontally means that each row of the image is reversed.  For example, flipping `[1, 1, 0]` horizontally results in `[0, 1, 1]`.

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting `[0, 1, 1]` results in `[1, 0, 0]`.

__Example 1:__
```
Input: [[1,1,0],[1,0,1],[0,0,0]]
Output: [[1,0,0],[0,1,0],[1,1,1]]
Explanation: First reverse each row: [[0,1,1],[1,0,1],[0,0,0]].
Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]
```
```javascript
var flipAndInvertImage = function(A) {
    A.forEach(arr => {
        let i = 0;
        let j = arr.length - 1;
        while(i <= j) {
            if(arr[i] === arr[j]){
                if(arr[i] === 1){
                    [arr[j], arr[i]] = [0, 0];
                }else {
                    [arr[i], arr[j]] = [1, 1];
                }
            }
            i++;
            j--;
        }
    })
    return A;
};
```
- two pointers: i, j
- if `arr[i]` is the same as `arr[j]`, after they reverse, they will be unchanged. So I only need to invert them.
- if `arr[i]` is different to `arr[j]`, they will be different after they reverse, but will be unchanged after they invert. So I don't need to anything on them.
