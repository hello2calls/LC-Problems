## 667. Beautiful Arrangement II (Medium)
Given two integers `n` and `k`, you need to construct a list which contains `n` different positive integers ranging from `1` to `n` and obeys the following requirement:
Suppose this list is [a1, a2, a3, ... , an], then the list [|a1 - a2|, |a2 - a3|, |a3 - a4|, ... , |an-1 - an|] has exactly `k` distinct integers.

If there are multiple answers, print any of them.

__Example 1:__
```
Input: n = 3, k = 1
Output: [1, 2, 3]
Explanation: The [1, 2, 3] has three different positive integers ranging from 1 to 3, and the [1, 1] has exactly 1 distinct integer: 1.
```
__Example 2:__
```
Input: n = 3, k = 2
Output: [1, 3, 2]
Explanation: The [1, 3, 2] has three different positive integers ranging from 1 to 3, and the [2, 1] has exactly 2 distinct integers: 1 and 2.
```
**Note:**
The n and k are in the range 1 <= k < n <= 104.

__Solution:__
When k = n-1, a valid construction is [1, n, 2, n-1, 3, n-2, ....]. One way to see this is, we need to have a difference of n-1, which means we need 1 and n adjacent; then, we need a difference of n-2, etc.

Also, when \text{k = 1}k = 1, a valid construction is [1, 2, 3, ..., n]. So we have a construction when n-k is tiny, and when it is large. This leads to the idea that we can stitch together these two constructions: we can put [1, 2, ..., n-k-1] first so that n is effectively k+1, and then finish the construction with the first "k = n-1" method.

For example, when n = 6 and \text{k = 3}k = 3, we will construct the array as [1, 2, 3, 6, 4, 5]. This consists of two parts: a construction of [1, 2] and a construction of [1, 4, 2, 3] where every element had 2 added to it (i.e. [3, 6, 4, 5]).

```js
var constructArray = function(n, k) {
    let arr1 = [];
    for(let i=1; i <= n-k-1; i++){
        arr1.push(i);
    }
    let num = 1;
    n = n - arr1.length;
    let arr2 = [];
    for(let i=0; i<n; i++){
        if(i % 2 === 0){
            arr2.push(num)
        }else{
            arr2.push(n-num+1);
            num+= 1;
        }
    }

    for(let i=0; i<arr2.length; i++){
        if(arr1.length > 0) arr2[i] += arr1[arr1.length - 1];
    }

    return arr1.concat(arr2);
};
```
