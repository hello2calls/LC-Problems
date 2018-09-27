## 717. 1-bit and 2-bit Characters (Easy)
We have two special characters. The first character can be represented by one bit `0`. The second character can be represented by two bits (`10` or `11`).

Now given a string represented by several bits. Return whether the last character must be a one-bit character or not. The given string will always end with a zero.

__Examples:__
```
Input:
bits = [1, 0, 0]
Output: True
Explanation:
The only way to decode it is two-bit character and one-bit character. So the last character is one-bit character.

Input:
bits = [1, 1, 1, 0]
Output: False
Explanation:
The only way to decode it is two-bit character and two-bit character. So the last character is NOT one-bit character.
```

__Solution:__
- start from the first element, if the element is `0`, it means this is one bit character. if it is `1`, this is two bits character.
- increment the idx by 1 if it is `0`, by 2 if it is `1`.

```JavaScript
var isOneBitCharacter = function(bits) {
    let idx = 0;
    while(idx < bits.length - 1){
        idx += bits[idx] + 1;
    }
    return idx === bits.length - 1;
};
```
