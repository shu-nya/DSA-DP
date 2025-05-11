# 🧠 LeetCode #509 - Fibonacci Number

## This document explains and solves the Fibonacci problem using multiple approaches with full step-by-step breakdowns, pseudocode, complexities, memory insights, and interview-oriented variations.

## 🧾 Problem Statement

> Given an integer `n`, return the `n`-th Fibonacci number:
>
> ```
> F(0) = 0
> F(1) = 1
> F(n) = F(n - 1) + F(n - 2), for n > 1
> ```

---

## ✅ Step 1: Brute-Force Recursion

### 💡 Explanation

Use the recursive definition directly.

### 🧾 Pseudocode

function fib(n):
if n == 0: return 0
if n == 1: return 1
return fib(n - 1) + fib(n - 2)

### 📊 Time Complexity: `O(2^n)`

### 🧠 Space Complexity: `O(n)` (call stack)

---

## ✅ Step 2: Recursion + Memoization (Top-Down DP)

### 💡 Explanation

Use a memo array to avoid recomputation.

### 🧾 Pseudocode

memo = array of size n+1 filled with -1
function fib(n):
if n == 0: return 0
if n == 1: return 1
if memo[n] ≠ -1:
return memo[n]
memo[n] = fib(n - 1) + fib(n - 2)
return memo[n]

### 📊 Time: `O(n)`

### 🧠 Space: `O(n)` (memo + stack)

---

## ✅ Step 3: Tabulation (Bottom-Up DP)

### 💡 Explanation

Fill a DP array iteratively.

### 🧾 Pseudocode

function fib(n):
if n == 0: return 0
dp = array of size n+1
dp[0] = 0
dp[1] = 1
for i = 2 to n:
dp[i] = dp[i-1] + dp[i-2]
return dp[n]

### 📊 Time: `O(n)`

### 🧠 Space: `O(n)`

---

## ✅ Step 4: Space Optimized DP

### 💡 Explanation

Only store the last two Fibonacci numbers.

### 🧾 Pseudocode

function fib(n):
if n == 0: return 0
prev2 = 0
prev1 = 1
for i = 2 to n:
curr = prev1 + prev2
prev2 = prev1
prev1 = curr
return prev1

### 📊 Time: `O(n)`

### 🧠 Space: `O(1)`

---

## ✅ Step 5: Matrix Exponentiation

### 💡 Explanation

Use matrix power to compute Fib in log(n) time.

### 📊 Time: `O(log n)`

### 🧠 Space: `O(1)`

---

## 🔁 How to Identify it as a DP Problem

| Clue                  | Insight             |
| --------------------- | ------------------- |
| Repeated subproblems  | Use memoization     |
| Overlapping recursion | Use DP              |
| Optimal substructure  | DP fits             |
| Large `n` values      | Optimize time/space |

---

## 🧠 Interview Variations

| Variation          | Description              |
| ------------------ | ------------------------ |
| Climb Stairs       | Steps like Fibonacci     |
| k-step jumps       | Generalized recurrence   |
| Modulo constraints | Use `%` in each step     |
| Print series       | Store full DP table      |
| Even/Odd Fib sum   | Track conditions in loop |

---

## 🧠 Memory Notes (C++/C)

- Use `std::vector` to avoid manual memory handling
- Be cautious of recursion limits
- Use `const &` where applicable

---

## ✅ Summary

| Approach        | Time     | Space | Notes                   |
| --------------- | -------- | ----- | ----------------------- |
| Brute Force     | O(2^n)   | O(n)  | Slow and impractical    |
| Memoization     | O(n)     | O(n)  | Fast, recursive         |
| Tabulation      | O(n)     | O(n)  | Safe and iterative      |
| Space Optimized | O(n)     | O(1)  | Best practical solution |
| Matrix Power    | O(log n) | O(1)  | Best for very large `n` |

---

## ✅ Best Practice

Use **space-optimized DP** unless the problem has constraints that require faster algorithms like **matrix exponentiation**.
