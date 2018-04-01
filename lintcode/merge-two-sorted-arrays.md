#  [Merge Two Sorted Arrays](http://www.lintcode.com/en/problem/merge-two-sorted-arrays/)

## Description

Merge two given sorted integer array A and B into a new sorted integer array.

**Example**

A = `[1, 2, 3]`
B = `[2, 4, 5, 6]`

OUTPUT = `[1,2,2,3,4,4,5,6]`

## Solution

### First Pass

```python
def mergeSortedArray(self, A, B):
    result = []
    i = j = 0
    while i < len(A) and j < len(B):
        if A[i] < B[j]:
            result.append(A[i])
            i += 1
        else:
            result.append(B[j])
            j += 1
    if i < len(A):
        result += A[i:]
    if j < len(B):
        result += B[j:]
    return result
```

### Second Pass

**How can you optimize your algorithm if one array is very large and the other is very small?**

```python
def mergeSortedArray(self, A, B):
    from bisect import bisect_right

    small_arr = large_arr = None
    if len(A) < len(B):
        small_arr, large_arr = A, B
    else:
        small_arr, large_arr = B, A

    i = 0
    result = []
    for num in small_arr:
        pos = bisect_right(large_arr, num)
        result += large_arr[i:pos]
        result.append(num)
        i = pos
    result += large_arr[i:]

    return result
```