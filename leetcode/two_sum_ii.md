# Two Sum II

## [Description](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)

Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have exactly one solution and you may not use the same element twice.

Input: numbers={2, 7, 11, 15}, target=9
Output: index1=1, index2=2 


## Solution

```python
def twoSumII(nums, target):
    if not nums:
        raise ValueError('Nums is None')
    l, r = 0, len(nums) - 1
    while l < r:
        total = nums[l] + nums[r]
        if total == target:
            return [l+1, r+1]
        elif total < target:
            l += 1
        else:
            r -= 1
    return [-1, -1]
```