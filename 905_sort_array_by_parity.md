## 905. Sort Array By Parity（Easy)
Given an array `A` of non-negative integers, return an array consisting of all the even elements of `A`, followed by all the odd elements of `A`.

#### my solution:

```javascript
var sortArrayByParity = function(A) {
    let idx = 0;
    for(let i = 0; i < A.length; i++){
        if(A[i] % 2 === 0){
            [A[idx], A[i]] = [A[i], A[idx]];
            idx += 1;
        }
    }
    return A;
};
```

start with a variable `idx`, set it to 0 as starting point. Iterate the arr once :
- if arr[i] is even number, swap `arr[i]` and `arr[idx]`, `idx++`

at the end, the left side of `arr[idx]` contains all even number.


#### leetcode inplace-sort solution:

we have two pointers `i`and `j`, `i` starts at 0, `j` starts at `arr.length - 1`.

Then, there are 4 cases for (`A[i] % 2, A[j] % 2`):
- If it is `(0, 1)`, then everything is correct: `i++ and j--`.
- If it is `(1, 0)`, we swap them so they are correct, then continue.
- If it is `(0, 0)`, only the i place is correct, so we `i++` and continue.
- If it is `(1, 1)`, only the j place is correct, so we `j--` and continue.


#### overall
Time complexity in both solution would be O(n), and Space complexity would be O(1).
