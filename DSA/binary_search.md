# Binary Search

If `n` is between 1 and 100, it is best to start from 50, i.e., choose the middle one.

To find a number > 50, we search after 50.
To find a number < 50, we search before 50.
If the number = 50, we have found 50.

How many steps are needed? -> log₂(n)
Basically, 2 to the power ... as you are dividing by 2 and so on and so forth.

Why is it called binary search?
Because we are doing things in base 2, that's why it's called binary - either left or right, two choices.

```python
def binary_search(to_find: int, arr: list) -> int:
    low = 0
    high = len(arr) - 1
    while low <= high:
        mid = (high + low) // 2
        if arr[mid] < to_find:
            low = mid + 1
        elif arr[mid] > to_find:
            high = mid - 1
        else:
            return mid
    return -1
```