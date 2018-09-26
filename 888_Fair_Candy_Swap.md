## 888. Fair Candy Swap (Easy)
Alice and Bob have candy bars of different sizes:` A[i]` is the size of the i-th bar of candy that Alice has, and `B[j]` is the size of the j-th bar of candy that Bob has.

Since they are friends, they would like to exchange one candy bar each so that after the exchange, they both have the same total amount of candy.  (The total amount of candy a person has is the sum of the sizes of candy bars they have.)

Return an integer array ans where `ans[0]` is the size of the candy bar that Alice must exchange, and `ans[1]` is the size of the candy bar that Bob must exchange.

If there are multiple answers, you may return any one of them.  It is guaranteed an answer exists.

__Example 1:__
```
Input: A = [1,1], B = [2,2]
Output: [1,2]
```
__my ruby solution:__
```ruby
def fair_candy_swap(a, b)
    sum_a = a.reduce(:+)
    sum_b = b.reduce(:+)
    hash_b = {}
    b.each {|n| hash_b[n] = true}
    add_num = (sum_b - sum_a) / 2
    a.each do |num|
        b_num = num + add_num
        return [num, b_num] if hash_b[b_num]
    end
end
```
If Alice gives candy x, and receives candy y, then Bob receives candy x and gives candy y. Then, we must have:
__Sa - x + y = Sb + x - y__
=>
__y = x + ((Sb - Sa) / 2)__
