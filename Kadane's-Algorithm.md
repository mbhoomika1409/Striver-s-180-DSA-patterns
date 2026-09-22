# 12. Kadane's Algorithm

## Problem

Given an integer array `nums`, find the **subarray with the largest sum** and return the sum of the elements present in that subarray.

A **subarray** is a contiguous, non-empty sequence of elements within an array.

---

## Example 1

**Input:**

```text
nums = [2, 3, 5, -2, 7, -4]
```

**Output:**

```text
15
```

**Explanation:**

The subarray `[2, 3, 5, -2, 7]` has the largest sum.

```text
2 + 3 + 5 - 2 + 7 = 15
```

---

## Example 2

**Input:**

```text
nums = [-2, -3, -7, -2, -10, -4]
```

**Output:**

```text
-2
```

**Explanation:**

When all numbers are negative, the largest sum is the largest individual element.

```text
[-2]
```

So the answer is `-2`.

---

## Your Turn

**Input:**

```text
nums = [-1, 2, 3, -1, 2, -6, 5]
```

**Output:**

```text
6
```

**Explanation:**

The subarray:

```text
[2, 3, -1, 2]
```

has the maximum sum.

```text
2 + 3 - 1 + 2 = 6
```

---

## Approach: Kadane's Algorithm

Kadane's Algorithm finds the maximum subarray sum in **O(n)** time.

We maintain two variables:

* `current_sum` → maximum sum ending at the current position
* `max_sum` → maximum sum found so far

### Main Idea

For every element, we decide:

```text
Start a new subarray
OR
Continue the previous subarray
```

We use:

```python
current_sum = max(num, current_sum + num)
```

Then update:

```python
max_sum = max(max_sum, current_sum)
```

---

## Python Solution

```python
class Solution:
    def maxSubArray(self, nums):
        current_sum = nums[0]
        max_sum = nums[0]

        for num in nums[1:]:
            current_sum = max(num, current_sum + num)
            max_sum = max(max_sum, current_sum)

        return max_sum
```

---

## Dry Run

For:

```text
nums = [-1, 2, 3, -1, 2, -6, 5]
```

| Number | Current Sum | Max Sum |
| -----: | ----------: | ------: |
|     -1 |          -1 |      -1 |
|      2 |           2 |       2 |
|      3 |           5 |       5 |
|     -1 |           4 |       5 |
|      2 |           6 |       6 |
|     -6 |           0 |       6 |
|      5 |           5 |       6 |

Therefore:

```text
Answer = 6
```

---

## Why Kadane's Algorithm?

A brute-force approach would check every possible subarray, which takes **O(n²)** or worse.

Kadane's Algorithm only scans the array once.

### Complexity

```text
Time Complexity:  O(n)
Space Complexity: O(1)
```

---

## Key Point to Remember

The most important line is:

```python
current_sum = max(num, current_sum + num)
```

Meaning:

```text
Should I start a new subarray from this number?
OR
Should I continue the previous subarray?
```

If starting fresh is better, start again.

Otherwise, continue the existing subarray.

---

## Interview Follow-up

### 1. How do you return the actual subarray?

Keep track of:

```text
start
end
```

indices along with the maximum sum.

### 2. How can Kadane's Algorithm be used for 2D arrays?

For a matrix, Kadane's Algorithm can be combined with column/row compression to find the maximum-sum rectangular submatrix.

---

## Pattern

```text
Maximum Subarray
        ↓
Kadane's Algorithm
        ↓
Track current best
        ↓
Track global best
```

### Final Formula

```python
current_sum = max(num, current_sum + num)
max_sum = max(max_sum, current_sum)
```
