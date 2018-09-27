## 167. Two Sum II - Input array is sorted (Easy)
Given an array of integers that is already *__sorted in ascending order__*, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.
__Note:__
 - Your returned answers (both index1 and index2) are not zero-based.
 - You may assume that each input would have exactly one solution and you may not use the same element twice.

 __Example:__
 ```
 Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.
 ```
 __My Solution:__
 - make a hash, the number is the key, index is the value.
 - iterate the numbers, and use target minus the current element, and see if we can find the remainder in our hash.
 ```JavaScript
var twoSum = function(numbers, target) {
    let hsh = {}
    for(let i=0; i < numbers.length; i++){
        if(hsh[numbers[i]]){
            hsh[numbers[i]].push(i+1)
        }else{
            hsh[numbers[i]] = [i+1];
        }
    }
    for(let i = 0; i < numbers.length; i++){
        if(hsh[target - numbers[i]]){
            if(target - numbers[i] === numbers[i]){
                return [hsh[numbers[i]][0], hsh[numbers[i]][1]];
            }else{
                return [hsh[numbers[i]][0], hsh[target - numbers[i]][0]];
            }
        }
    }
};
```
