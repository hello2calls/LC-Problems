## 495. Teemo Attacking (Medium)
In LOL world, there is a hero called Teemo and his attacking can make his enemy Ashe be in poisoned condition. Now, given the Teemo's attacking **ascending** time series towards Ashe and the poisoning time duration per Teemo's attacking, you need to output the total time that Ashe is in poisoned condition.

You may assume that Teemo attacks at the very beginning of a specific time point, and makes Ashe be in poisoned condition immediately.

__Example 1:__
```
Input: [1,4], 2
Output: 4
Explanation: At time point 1, Teemo starts attacking Ashe and makes Ashe be poisoned immediately.
This poisoned status will last 2 seconds until the end of time point 2.
And at time point 4, Teemo attacks Ashe again, and causes Ashe to be in poisoned status for another 2 seconds.
So you finally need to output 4.
```
__Example 2:__
```
Input: [1,2], 2
Output: 3
Explanation: At time point 1, Teemo starts attacking Ashe and makes Ashe be poisoned.
This poisoned status will last 2 seconds until the end of time point 2.
However, at the beginning of time point 2, Teemo attacks Ashe again who is already in poisoned status.
Since the poisoned status won't add up together, though the second poisoning attack will still work at time point 2, it will stop at the end of time point 3.
So you finally need to output 3.

```
__My Solution:__
- iterate the array from right to left. at the last time point, we can add the duration imediately.
- if it is not the last time point, we need to check if we add the duration time to current time point, the time point is greater than next time point or not. if it is greater, then we only add the time diff between current and next time point, if it is not greater we just add the duration time.
```js
var findPoisonedDuration = function(timeSeries, duration) {
    if(timeSeries.length === 0) return 0;
    let time = duration;
    for(let i = timeSeries.length-2; i>=0; i--){
        if(timeSeries[i] + duration > timeSeries[i+1]){
            time += timeSeries[i+1] - timeSeries[i];
        }else {
            time += duration;
        }
    }
    return time
};
```
