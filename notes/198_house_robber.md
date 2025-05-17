# 🧠 LeetCode #198 - House Robber

## This document explains and solves the House Robber problem using multiple approaches with full step-by-step breakdowns, pseudocode, complexities, memory insights, and interview-oriented variations.

## 🧾 Problem Statement

> You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, but adjacent houses have connected security systems that will alert the police if both are robbed on the same night.
>
> Given an integer array `nums` representing the amount of money in each house, return the maximum amount you can rob tonight **without alerting the police**.

---

## ✅ Step 1: Brute-Force Recursion

### 💡 Explanation

Try all combinations of skipping or robbing each house.

### 🧾 Pseudocode

```python
function robFrom(i):
    if i >= n: return 0
    return max(
        robFrom(i + 1),
        nums[i] + robFrom(i + 2)
    )

📊 Time Complexity: O(2^n)
🧠 Space Complexity: O(n) (recursion stack)
✅ Step 2: Tabulation (Bottom-Up DP)
💡 Explanation
Build a dp array where dp[i] stores the max amount you can rob starting from house i.

🧾 Pseudocode

function rob(nums):
    n = len(nums)
    dp = array of size n+2 filled with 0
    for i from n-1 to 0:
        dp[i] = max(dp[i+1], nums[i] + dp[i+2])
    return dp[0]

📊 Time Complexity: O(n)
🧠 Space Complexity: O(n)
✅ Step 3: Space Optimized DP
💡 Explanation
We only need the last two results at each step (dp[i+1] and dp[i+2]), so we can optimize to O(1) space.

🧾 Pseudocode

function rob(nums):
    prev1 = 0
    prev2 = 0
    for i from n-1 to 0:
        curr = max(prev1, nums[i] + prev2)
        prev2 = prev1
        prev1 = curr
    return prev1

📊 Time Complexity: O(n)
🧠 Space Complexity: O(1)

🔁 How to Identify it as a DP Problem
Clue	Insight
Cannot rob adjacent	Problem has overlapping decisions
Maximize money robbed	Optimization → likely DP
Substructure recurrence	Use DP or recursion
Large input size	Avoid brute force; optimize

🧠 Interview Variations

Variation	Description
House Robber II	Houses are in a circle
House Robber III	Houses are in a binary tree
Skip k houses	Rob one, skip k neighbors
Print robbed houses	Backtrack to reconstruct choices
Add cooldown/penalty	Requires constraint tracking in recurrence

✅ Summary
Approach	Time	Space	Notes
Brute Force Recursion	O(2^n)	O(n)	Simple but inefficient
Tabulation (Bottom-Up)	O(n)	O(n)	Clean iterative solution
Space Optimized DP	O(n)	O(1)	✅ Best practical and interview use
```
