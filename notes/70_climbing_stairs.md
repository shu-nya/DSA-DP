# 🧗 LeetCode #70 - Climbing Stairs

## 🎯 Problem Summary

You’re climbing a staircase with `n` steps.
You can take **1 step or 2 steps** at a time.
Return how many **distinct ways** you can reach the top.

---

## 🧠 Insight: Fibonacci-style DP

Let’s define:

- `ways(n)` = number of distinct ways to reach step `n`

To reach step `n`, you could:

- Come from `n - 1` by taking **1 step**
- Come from `n - 2` by taking **2 steps**

### ✅ Recurrence Relation:

ways(n) = ways(n - 1) + ways(n - 2)

### 🧱 Base Cases:

---

# ✅ Step-by-Step Approaches

---

## ✅ 1. Brute Force Recursion

### 💡 Explanation:

Try all combinations recursively — very inefficient.

### 🔁 Pseudocode:

```python
function climb(n):
    if n == 0 or n == 1:
        return 1
    return climb(n - 1) + climb(n - 2)

📊 Time Complexity: O(2^n)
🧠 Space Complexity: O(n) (call stack)
⚠️ Drawbacks:
Recomputes the same subproblems

Stack overflow for large n

✅ 2. Memoization (Top-Down DP)
💡 Explanation:
Cache results using a memo array to avoid recomputation.

🔁 Pseudocode:

memo = array of size n+1 filled with -1
function climb(n):
    if n == 0 or n == 1: return 1
    if memo[n] ≠ -1: return memo[n]
    memo[n] = climb(n - 1) + climb(n - 2)
    return memo[n]

📊 Time: O(n)
🧠 Space: O(n) (memo + stack)
✅ 3. Tabulation (Bottom-Up DP)
💡 Explanation:
Build the solution iteratively from the base.

🔁 Pseudocode:

dp[0] = 1
dp[1] = 1
for i = 2 to n:
    dp[i] = dp[i - 1] + dp[i - 2]
return dp[n]

📊 Time: O(n)
🧠 Space: O(n)
✅ 4. Space-Optimized DP
💡 Explanation:
Use only two variables to track the previous values.

🔁 Pseudocode:

if n == 0 or n == 1: return 1
prev2 = 1
prev1 = 1
for i = 2 to n:
    curr = prev1 + prev2
    prev2 = prev1
    prev1 = curr
return prev1

📊 Time: O(n)
🧠 Space: O(1)

📌 Summary Comparison
Approach	Time	Space	Description
Brute Force	O(2^n)	O(n)	Simple recursion, very slow
Memoization	O(n)	O(n)	Recursive with caching
Tabulation	O(n)	O(n)	Iterative with full DP array
Space-Optimized DP	O(n)	O(1)	✅ Best approach (low memory + fast)
```
