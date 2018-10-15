## 914. X of a Kind in a Deck of Cards (Easy)
In a deck of cards, each card has an integer written on it.

Return `true` if and only if you can choose `X >= 2` such that it is possible to split the entire deck into 1 or more groups of cards, where:

 - Each group has exactly `X` cards.
 - All the cards in each group have the same integer.

 __Example 1:__
 ```
 Input: [1,2,3,4,4,3,2,1]
Output: true
Explanation: Possible partition [1,1],[2,2],[3,3],[4,4]
 ```
 __Example 2:__
 ```
 Input: [1,1,1,2,2,2,3,3]
Output: false
Explanation: No possible partition.
 ```
 __Example 5:__
 ```
 Input: [1,1,2,2,2,2]
Output: true
Explanation: Possible partition [1,1],[2,2],[2,2]
 ```
 __Solution:__
Say there are `C_i` cards of number `i`. These must be broken down into piles of `X` cards each, ie. `C_i` % `X` == 0 for all `i`.

Thus, `X` must divide the greatest common divisor of `C_i`. If this greatest common divisor `g` is greater than 1, then `X` = `g` will satisfy. Otherwise, it won't.

```ruby
def has_groups_size_x(deck)
    hsh = Hash.new(0)
    deck.each {|el| hsh[el] += 1}

    num = -1
    hsh.values.each do |val|
        return false if val < 2
        if num == -1
            num = val
        else
            num = val.gcd(num)
        end
        return false if num < 2
    end
    true
end
```
