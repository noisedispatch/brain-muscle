# [Two Sum](https://leetcode.com/problems/two-sum/description/)

## Description

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

## Solution

```python
def twoSum(nums, target):
    if not nums:
        raise ValueError('Input array is None')
    seen = {}
    for (i, num) in enumerate(nums):
        result = target - num
        if result in seen:
            return [seen[result], i]
        seen[num] = i
    return [-1, -1]
```