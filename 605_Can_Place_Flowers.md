## 605. Can Place Flowers (Esay)
Suppose you have a long flowerbed in which some of the plots are planted and some are not. However, flowers cannot be planted in adjacent plots - they would compete for water and both would die.

Given a flowerbed (represented as an array containing 0 and 1, where 0 means empty and 1 means not empty), and a number n, return if **n** new flowers can be planted in it without violating the no-adjacent-flowers rule.

__Example 1:__
```
Input: flowerbed = [1,0,0,0,1], n = 1
Output: True
```
__Example 2:__
```
Input: flowerbed = [1,0,0,0,1], n = 2
Output: False
```
__My Solution:__
```ruby
def can_place_flowers(flowerbed, n)
    idx = 0
    until n == 0
        if idx == flowerbed.length
            return false
        elsif idx == 0 && flowerbed[idx] == 0 && flowerbed[idx+1] == 0
            n -= 1
            flowerbed[idx] = 1
        elsif idx == flowerbed.length - 1 && flowerbed[idx] == 0 && flowerbed[idx-1] == 0
            n -= 1
            flowerbed[idx] = 1
        elsif flowerbed[idx-1] == 0 && flowerbed[idx] == 0 && flowerbed[idx+1] == 0
            flowerbed[idx] = 1
            n -= 1
        end
        idx += 1
    end

    true
end
```
