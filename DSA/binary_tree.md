# Binary Tree

## Tree Traversals
1. **Pre-order**: Root → Left → Right
2. **In-order**: Left → Root → Right
3. **Post-order**: Left → Right → Root

## Pre order
```typescript
function walk(curr: BinaryNode<number> | undefined ,path: number[]): number[]{
if (!curr){
    return path;
}
path.push(curr.value)

}
export default function pre_order_search(head: BinaryNode<number>): number[]{
    return walk(head, [])

}
```