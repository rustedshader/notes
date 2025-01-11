# Tree Data Structure

## Basic Terminology
- **Root**: The topmost node in a tree
- **Height**: The length of the longest path from root to leaf
- **Depth**: The length of path from root to current node
- **Binary Tree**: A tree where each node has at most 2 children (0-2 children)
- **General Tree**: A tree where nodes can have any number of children
- **Binary Search Tree (BST)**: A binary tree where:
    - Left subtree contains nodes with values less than parent
    - Right subtree contains nodes with values greater than parent
    - Enables efficient searching, insertion and deletion operations
- **Leaf Node**: A node without any children (terminal node)
- **Balanced Tree**: A tree where the heights of left and right subtrees of any node differ by at most one
- **Branching Factor**: Maximum number of children a node can have

## Tree Traversals
1. **Pre-order** (Root → Left → Right):
   - Visit current node first, then traverse left subtree, finally traverse right subtree
   - Useful for creating a copy of the tree or serializing tree structure

2. **In-order** (Left → Root → Right):
   - Traverse left subtree, visit current node, then traverse right subtree
   - In BST, gives nodes in ascending order
   - Common in binary search trees for sorted traversal

3. **Post-order** (Left → Right → Root):
   - Traverse left subtree, traverse right subtree, then visit current node
   - Useful for deleting tree or evaluating expressions

### Common Applications
- File systems: Directory structure
- Database indexing: B-trees and B+ trees
- Family trees: Hierarchical relationships
- Organization charts: Company structure
- Abstract Syntax Trees: Compiler design
- Decision Trees: Machine Learning

## Code Implementation

### Pre-order Traversal
```typescript
function walk(curr: BinaryNode<number> | null, path: number[]): number[] {
    // Base case: if current node is null, return path
    if (!curr) {
        return path;
    }
    
    // Pre-order: Process current node before children
    path.push(curr.value);
    
    // Recursively process left and right subtrees
    walk(curr.left, path);
    walk(curr.right, path);
    
    return path;
}

export default function pre_order_search(head: BinaryNode<number>): number[] {
    return walk(head, []);
}
```

The pre-order traversal implementation:
1. Takes a binary tree node and an array to store the path
2. Processes current node first by adding its value to path
3. Recursively traverses left and right subtrees
4. Returns array containing node values in pre-order sequence

Time Complexity: O(n) where n is number of nodes
Space Complexity: O(h) where h is height of tree for recursion stack


# Tree is an abstract data type (ADT)
An ADT is a data type that is defined by set of values but not how to implement them

# What is the difference between binary tree and binary search tree
In binary search tree all the elements on the left are smaller than the root node
and all the elements on the right are bigger than the root node 
There time complexity is of log base 2 of N as it splits half each itteration
