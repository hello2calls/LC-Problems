## 521. Longest Uncommon Subsequence I (easy)

Given a group of two strings, you need to find the longest uncommon subsequence of this group of two strings. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings.

A __subsequence__ is a sequence that can be derived from one sequence by deleting some characters without changing the order of the remaining elements. Trivially, any string is a subsequence of itself and an empty string is a subsequence of any string.

The input will be two strings, and the output needs to be the length of the longest uncommon subsequence. If the longest uncommon subsequence doesn't exist, return -1.

__Example 1:__
```
Input: "aba", "cdc"
Output: 3
Explanation: The longest uncommon subsequence is "aba" (or "cdc"),
because "aba" is a subsequence of "aba",
but not a subsequence of any other strings in the group of two strings.
```

__my solution__
```JavaScript
var findLUSlength = function(a, b) {
    if(a === b) return -1;
    if(a !== b && a.length === b.length) return a.length;
    return Math.max(a.length, b.length);

};
```

__Complexity__
Time complexity : O(min(x,y))O(min(x,y)). where x and y are the lengths of strings a and b respectively. Here equals method will take min(x,y)min(x,y) time .
