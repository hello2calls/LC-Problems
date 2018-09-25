## 896. Monotonic Array (Easy)
An array is monotonic if it is either monotone increasing or monotone decreasing.

An array `A` is monotone increasing if for all `i <= j, A[i] <= A[j]`.  An array A is monotone decreasing if for all `i <= j, A[i] >= A[j]`.

Return `true` if and only if the given array `A` is monotonic.

__Example 1:__
```
Input: [1,2,2,3]
Output: true
```
__my ruby solution:__
```ruby
def is_monotonic(a)
    return true if a.length < 3
    pre_inc = nil
    inc = nil
    (1..a.length - 1).each do |i|
        if a[i] > a[i-1]
            inc = true
        elsif a[i] < a[i-1]
            inc = false
        end
        pre_inc = inc if pre_inc.nil?
        return false if pre_inc != inc
    end
    true

end
```

- pre_inc will be changed only if it is nil
- if `pre_inc` is diff to `inc`, return false immediately
