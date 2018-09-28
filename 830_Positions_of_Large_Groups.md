## 830. Positions of Large Groups (Easy)
In a string `S` of lowercase letters, these letters form consecutive groups of the same character.

For example, a string like `S = "abbxxxxzyy"` has the groups `"a"`, `"bb"`, `"xxxx"`, `"z"` and `"yy"`.

Call a group large if it has 3 or more characters.  We would like the starting and ending positions of every large group.

The final answer should be in lexicographic order.

__Examples:__
```
Input: "abbxxxxzzy"
Output: [[3,6]]
Explanation: "xxxx" is the single large group with starting  3 and ending positions 6.

Input: "abcdddeeeeaabbbcd"
Output: [[3,5],[6,9],[12,14]]
```
__My Solution:__
- variable `start` tracking start index of every group.
- variable `char` tracking the character of current group
- if `S[i]` is diff from current `char`, it means current group is endded, we will push the indices to result array if the length is greater than 3, and then set new starting index to current index and `char` to current letter.
```JavaScript
var largeGroupPositions = function(S) {
    let result = [];
    let start = 0;
    let char = S[0];
    for(let i = 1; i <= S.length; i++){
        if(S[i] !== char){
            if(i - start >= 3) result.push([start, i - 1]);
            start = i;
            char = S[i];
        }
    }
    return result;
};
```
