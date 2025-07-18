# -Problems-of-the-Week-POW-DSA
In this we solved problems not by approching but optimization of code is very important.
17-7-25
 📝 Problem Statement
Given a rotated sorted array (ascending sorted array rotated at an unknown pivot), find the minimum element in O(log N) time.

📌 Input Format
First line: Integer N (number of elements)

Second line: N space-separated integers — the rotated sorted array

📌 Output Format
A single integer: the minimum element of the rotated array

✅ Constraints
1 <= N <= 10^5

-10^9 <= A[i] <= 10^9

No duplicate elements

The array is a rotated version of a sorted array

🧠 Approach: Binary Search (O(log N))
Key Idea:
Since the array was originally sorted, but then rotated, the minimum element will be the only point where the next element is greater than the current.

Use binary search to narrow down the section of the array that might contain the minimum.

🔁 Steps:
Initialize: low = 0, high = N-1

Loop while low < high:

mid = (low + high) / 2

If arr[mid] > arr[high]: Minimum is right of mid, so low = mid + 1

Else: Minimum is at mid or to the left, so high = mid

When loop exits, low == high, return arr[low]

🕒 Time Complexity:
O(log N) due to binary search

💾 Space Complexity:
O(1) constant space

| **Aspect**              | **Previous Approach**                                           
| **What Changed / Why**                                                         
| ----------------------- | -------------------------------------- 
| **Binary Search Logic** | `mid = low + (high - low) / 2`                                                                     

**unsigned right shift** `>>>` as a faster and safe midpoint calculation  
| **Input Reading Loop**  | `for (int i = 0; i < n; i++) { arr[i] = sc.nextInt(); }`           
| **Code Formatting**     | Traditional multiline block formatting                                       
| **Scanner Closing**     | `sc.close()` manually                                                                      
| **Return Statement**    | `return arr[low];`                                                                                                                                                              
| **Binary Search Logic** | `if (arr[mid] > arr[high]) { low = mid + 1; } else { high = mid; }` | `if (arr[mid] > arr[high]) low = mid + 1; else high = mid;` | Same logic; used **no braces for short if/else**                                  
| **Comments**            | Present for explanation                                                                                                                       
| **Performance**         | `O(log N)` time, `O(1)` space                                                                                      | No performance change (still optimal)                                        

-----------------------------------------------------------------------------------------------------------------------------------------------
🧾 Problem Statement:
You are a data analyst for a fitness app. Every day, users log the number of calories burned. Your goal is to identify streaks (subarrays) where the total calories burned equals a specific target k.

Given: An integer array nums[] representing calories burned per day.An integer k, the target calorie goal
Return: The total number of continuous subarrays whose sum equals exactly k
🔢 Example
Input:
nums = [1, 2, 3]
k = 3
Output:
Copy
Edit
2
Explanation:
Two subarrays sum to 3:
[1, 2]
[3]
✅ Brute Force Approach
🔍 Description:
Loop through all possible subarrays, compute the sum for each, and check if it equals k.

🔁 Steps:
Use two nested loops:
Outer loop: start index
Inner loop: end index, accumulate the sum
Count subarrays where the sum is k.
Time Complexity: O(n²)
💾 Space Complexity: O(1)
Optimized Approach — Prefix Sum + HashMap
🔍 Description:
Instead of checking all subarrays, track cumulative (prefix) sums and use a HashMap to store how often a prefix sum has occurred.
If the current prefix sum is sum and we want a subarray sum equal to k, then we need:We check how many times sum - k has occurred — that gives us the number of subarrays ending at current index with sum k.Optimization Steps:
Step	Action
1.	Initialize sum = 0, count = 0
2.	Create a HashMap to store prefix sum frequencies. Add base case: map.put(0, 1)
3.	Traverse array. For each num:
→ sum += num
→ Check if (sum - k) is in map
→ If yes, add its frequency to count
→ Update map.put(sum, freq + 1)
4.	Return countTime Complexity: O(n)
💾 Space Complexity: O(n) (HashMapComparison Table
Feature	Brute Force	Optimized (Prefix Sum + Map)
Time Complexity	O(n²)	O(n)
Space Complexity	O(1)	O(n)
Uses HashMap	❌	✅
Suitable for large input	❌	✅
Reusable Prefix Data	❌	✅
-----------------------------------------------------------------------------------------------------------------------------------------------
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
 
