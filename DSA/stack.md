# Stack

A stack is a Last-In-First-Out (LIFO) data structure that can be implemented using a linked list. Unlike a queue, operations are performed only at one end (head).

## Structure
- Each node contains:
    - value: of type T
    - next: pointer to the next node
    - prev: (optional) for double linked lists

## Visual Representation
```
Queue:    head-> A -> B -> C -> D <-tail

Stack:    E
                 |
                 v
                 A <- B <- C <- D <-head
```
## Implementation

Below is a TypeScript implementation of a Stack using a singly-linked structure:

```typescript
type Node<T> = {
    value: T,
    prev?: Node<T>,
}

export default class Stack<T> {
    public length: number;
    private head?: Node<T>;

    constructor() {
        this.head = undefined;
        this.length = 0;
    }

    push(item: T): void {
        // Create new node
        const node = { value: item } as Node<T>;
        this.length++;
        
        if (!this.head) {
            this.head = node;
            return;
        }
        
        // Link new node to current head
        node.prev = this.head;
        this.head = node;
    }

    pop(): T | undefined {
        this.length = Math.max(0, this.length - 1);
        
        if (this.length === 0) {
            const head = this.head;
            this.head = undefined;
            return head?.value;
        }
        
        const head = this.head as Node<T>;
        this.head = head.prev;
        return head.value;
    }

    peek(): T | undefined {
        return this.head?.value;
    }
}
```

### Explanation

Let's break down this Stack implementation step by step:

#### 1. Type Definition
```typescript
type Node<T> = {
    value: T,
    prev?: Node<T>,
}
```
- Defines a generic Node type that can store any type T
- Contains value of type T and optional reference to previous node
- Using `?` indicates prev is optional (can be undefined)

#### 2. Stack Class Structure
```typescript
export default class Stack<T> {
    public length: number;
    private head?: Node<T>;
```
- Generic class that works with any type T
- Tracks length publicly
- Maintains private head node reference
- Optional head (can be undefined)

#### 3. Core Methods

##### Constructor
```typescript
constructor() {
    this.head = undefined;
    this.length = 0;
}
```
- Initializes empty stack
- Sets head to undefined
- Sets initial length to 0

##### Push Method
```typescript
push(item: T): void {
    const node = { value: item } as Node<T>;
    this.length++;
    
    if (!this.head) {
        this.head = node;
        return;
    }
    
    node.prev = this.head;
    this.head = node;
}
```
## What's happening explanation

    node.prev = this.head;

    Takes the new node

    Sets its prev pointer to current head

    Links new node to existing chain

    this.head = node;

    Updates head to point to new node

    Makes new node the top of stack

    Completes the insertion

# Best Explanation >>>
```

// Initial stack: [3,2,1]
head → {value:3, prev→{value:2, prev→{value:1, prev→null}}}

// Push 4
node = {value:4, prev:null}
node.prev = this.head  // Links 4 to 3
this.head = node       // Makes 4 the new head

// Final stack: [4,3,2,1]
head → {value:4, prev→{value:3, prev→{value:2, prev→{value:1, prev→null}}}}
```
- Creates new node with given value
- Increments length
- For empty stack: makes new node the head
- Otherwise: links new node to current head and updates head

##### Pop Method
```typescript
pop(): T | undefined {
    this.length = Math.max(0, this.length - 1);
    
    if (this.length === 0) {
        const head = this.head;
        this.head = undefined;
        return head?.value;
    }
    
    const head = this.head as Node<T>;
    this.head = head.prev;
    return head.value;
}
```
- Decrements length (minimum 0)
- For empty stack: returns head value and clears head
- Otherwise: updates head to previous node and returns old head value

##### Peek Method
```typescript
peek(): T | undefined {
    return this.head?.value;
}
```
- Returns value of top element without removal
- Returns undefined if stack is empty

This implementation creates a Last-In-First-Out (LIFO) stack using a singly-linked list where nodes point to previous elements.


### Implementation Details

1. **Node Structure**:
   - Generic type `T` for flexible data types
   - Contains a value and an optional reference to previous node

2. **Stack Class Properties**:
   - `length`: Tracks number of elements
   - `head`: Reference to top element
   - Uses TypeScript generics for type safety

3. **Methods**:
   - `push`: O(1) - Adds element to top
   - `pop`: O(1) - Removes and returns top element
   - `peek`: O(1) - Views top element without removal

4. **Error Handling**:
   - Safe returns with undefined when empty
   - Length maintenance with Math.max to prevent negative counts


## Key Points
- Stack operations occur only at the head
- When a stack error occurs, the resulting error trace is called a "stacktrace"
- To add (push) element E to stack:
    1. New node E points to current head
    2. Update head to point to E

## Operations
- Push: Add element at head
- Pop: Remove element from head
- Peek/Top: View head element without removing


