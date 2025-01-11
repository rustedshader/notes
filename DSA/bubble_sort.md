# Bubble Sort

A simple comparison-based sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order.

## What is a Sorted Array?

An array is considered sorted when each element is less than or equal to its next element:
- For any index i: `array[i] ≤ array[i+1]`

## Time Complexity

- Worst Case: O(n²)
- Best Case: O(n) [when array is already sorted]
- Average Case: O(n²)

## Space Complexity
- O(1) - In-place sorting algorithm

## Implementation in JavaScript

```javascript
function bubbleSort(arr) {
    for (let i = 0; i < arr.length; i++) {
        // We subtract i because after each iteration, the last i elements are already sorted
        // This optimization reduces unnecessary comparisons
        for (let j = 0; j < arr.length - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap elements
                [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
            }
        }
    }
    return arr;
}
```

### Advantages
- Simple to understand and implement
- Requires no additional memory space

### Disadvantages
- Not suitable for large datasets
- Poor time complexity of O(n²)
