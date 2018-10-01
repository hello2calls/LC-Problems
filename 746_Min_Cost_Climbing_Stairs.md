## 746. Min Cost Climbing Stairs (Easy)
On a staircase, the `i`-th step has some non-negative cost `cost[i] `assigned (0 indexed).

Once you pay the cost, you can either climb one or two steps. You need to find minimum cost to reach the top of the floor, and you can either start from the step with index 0, or the step with index 1.

__Example:__
```
Input: cost = [1, 100, 1, 1, 1, 100, 1, 1, 100, 1]
Output: 6
Explanation: Cheapest is start on cost[0], and only step on 1s, skipping cost[3].
```

__My Solution:__
- use dynamic programming (bottom to top)
- in each step, the minimum cost to climbing to that step would be the smaller of the min-cost of `[i-1]`step and `[i-2]` step, plus the cost of itself.
- result array is tracking the minimum cost `result[i]` to climb to `i`-th stair.

```ruby
def min_cost_climbing_stairs(cost)
    result = [cost[0], cost[1]]
    (2...cost.length).each do |i|
        min_cost = [result[i-1]+cost[i], result[i-2]+cost[i]].min
        result << min_cost
    end

    [result[-1], result[-2]].min
end
```
