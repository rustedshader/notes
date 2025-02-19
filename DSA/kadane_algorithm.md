# Kadane Algorithm

Subarray with the largest sum

```python
def max_subarray(numbers):
    """Find the largest sum of any contiguous subarray."""
    best_sum = float('-inf')
    current_sum = 0
    for x in numbers:
        current_sum = max(x, current_sum + x)
        best_sum = max(best_sum, current_sum)
    return best_sum
```

```python
curr_sum = 0
max_sum = float('inf')
for i in range(len(arr)):
    curr_sum += arr[i]
    max_sum = max(max_sum , curr_sum)

    if curr_sum < 0:
        curr_sum = 0
return max_sum
```

The runtime complexity of Kadane's algorithm is O(n) and space complexity is O(1).