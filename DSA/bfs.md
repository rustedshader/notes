# Breadth First Search (BFS)

## Overview
BFS is a tree traversal algorithm that explores all vertices at the current depth before moving to vertices at the next depth level.

```
Level 0:          Root
                   |
Level 1:      Left--Right
                |      |
Level 2:    Left-Right Left-Right
```

## Characteristics
- Visits nodes level by level (horizontally)
- Uses a Queue data structure for processing
- Time Complexity: O(n) where n is number of nodes
- Space Complexity: O(w) where w is maximum width of tree

## Implementation Details
The TypeScript code below demonstrates BFS implementation:

```typescript
// Define the Binary Tree Node structure
declare type BinaryNode<T> = {
    value: T;
    left: BinaryNode<T> | null;
    right: BinaryNode<T> | null;
}

// BFS implementation to find a value in binary tree
export default function bfs(head: BinaryNode<number>, needle: number): boolean {
    // Initialize queue with root node
    const q: (BinaryNode<number> | null)[] = [head];

    // Process until queue is empty
    while (q.length) {
        // Remove first element from queue
        const curr = q.shift() as BinaryNode<number> | undefined | null;
        if (!curr) continue;

        // Check if current node has target value
        if (curr.value === needle) {
            return true;
        }

        // Add left and right children to queue
        q.push(curr.left);
        q.push(curr.right);
    }

    return false;
}
```

## Time Complexity Note
While BFS is O(n) in general, using JavaScript array as queue makes it O(n²) due to shift() operation being O(n). For better performance, use a proper queue implementation.
