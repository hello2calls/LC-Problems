## 661. Image Smoother (Easy)
Given a 2D integer matrix M representing the gray scale of an image, you need to design a smoother to make the gray scale of each cell becomes the average gray scale (rounding down) of all the 8 surrounding cells and itself. If a cell has less than 8 surrounding cells, then use as many as you can.

__Example:__
```
Input:
[[1,1,1],
 [1,0,1],
 [1,1,1]]
Output:
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]
Explanation:
For the point (0,0), (0,2), (2,0), (2,2): floor(3/4) = floor(0.75) = 0
For the point (0,1), (1,0), (1,2), (2,1): floor(5/6) = floor(0.83333333) = 0
For the point (1,1): floor(8/9) = floor(0.88888889) = 0
```
__Solution:__
- iterate through each square and then iterate through all surrounding square
```JavaScript
var imageSmoother = function(M) {
    let sum;
    let sq;
    let result = [];
    M.forEach(el => result.push([]));

    for(let R = 0; R < M.length; R++){
        for(let C = 0; C < M[0].length; C++){
            sum = 0;
            sq = 0
            for(let r = R-1; r <= R+1; r++){
                for(let c=C-1; c <= C+1; c++){
                    if(r >= 0 && r < M.length && c >= 0 && c < M[0].length){
                        sum += M[r][c];
                        sq++;
                    }
                }
            }
            result[R][C] = Math.floor(sum / sq);
        }
    }
    return result;
};
```
