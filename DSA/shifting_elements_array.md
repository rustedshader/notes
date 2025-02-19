# Shifting Elements of The Array

# Brute Force Method 

k times shift left

```python
for i in range(k):
    f = arr[0]
    for j in range(n-1):
        arr[i] = arr[i+1]
    arr[-1] = f
```

# Pythonic Way

```python
k = k % n 
arr = arr[k:] + arr[:k]
```