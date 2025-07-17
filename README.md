# -Problems-of-the-Week-POW-DSA
In this we solved problems not by approching but optimization of code is very important.
17-7-25

Q3
# Ruby Second House 🏠🎨

## Problem Statement

You are a construction manager overseeing the painting of a long row of houses.  
Each house must be painted one of several available colors. However, adjacent houses **cannot** have the same color to preserve aesthetic appeal.
Each painting option has a different cost.  
You are given a 2D matrix `costs`, where `costs[i][j]` represents the cost of painting house `i` with color `j`.
### Objectives:
- No two adjacent houses can have the same color.
- Minimize the total painting cost.
---
## 🧠 Approach

This problem is solved using **Dynamic Programming (DP)**.

We maintain a DP table `dp[i][j]` which stores the minimum cost to paint up to the `i-th` house with color `j`.

For each house `i` and color `j`, the cost is computed as:
dp[i][j] = costs[i][j] + min(dp[i - 1][m]) for all m ≠ j
Finally, we return the minimum value in the last row of the DP table, which represents the lowest cost to paint all houses following the constraints.

---

## ✅ Sample Input
java
int[][] costs = {
    {17, 2, 17},
    {16, 16, 5},
    {14, 3, 19}
};
Minimum cost to paint all houses: 10
Time & Space Complexity
Time Complexity: O(N × K²)
N = number of houses

K = number of colors
For each house, we compare each color with all other colors of the previous house.
Space Complexity: O(N × K)
We use a 2D array dp[N][K] to store minimum costs.
✅ Optimization Note:
we can reduce space complexity to O(K) by reusing a 1D array and tracking only the previous row.
Changes Made:
 We Used only two 1D arrays (prev and curr) instead of a 2D DP table.
At each step, curr[j] is updated based on the minimum of all previous colors except j.
After each iteration, prev = curr.
📊 Time & Space Complexity (Optimized)
Metric	Value
Time Complexity=	O(N × K²)
Space Complexity=O(K)
 
