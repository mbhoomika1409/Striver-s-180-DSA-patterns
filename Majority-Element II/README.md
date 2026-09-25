# Majority Element II

## Problem

Given an integer array `nums` of size `n`, find all elements that appear more than `⌊n / 3⌋` times.

## Approach

Use a **Hash Map (Dictionary)** to store the frequency of each element.

### Steps

1. Find the length of the array.
2. Count the frequency of every element using a dictionary.
3. Calculate `n // 3`.
4. Add elements whose frequency is greater than `n // 3` to the result.
5. Return the result.

## Example

### Input

```text
nums = [3, 2, 3]
```

### Frequency

```text
3 → 2
2 → 1
```

Since:

```text
n = 3
n // 3 = 1
```

Only `3` appears more than `1` time.

### Output

```text
[3]
```

## Python Solution

```python
class Solution:
    def majorityElement(self, nums):
        n = len(nums)
        count = {}
        result = []

        for num in nums:
            count[num] = count.get(num, 0) + 1

        for num in count:
            if count[num] > n // 3:
                result.append(num)

        return result
```

## Complexity

* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(n)`

## Key Learning

The important idea is to use a **dictionary to count frequencies**, then check which elements occur more than `n // 3` times.

```text
count → frequency of each element
n // 3 → required threshold
result → elements satisfying the condition
```
