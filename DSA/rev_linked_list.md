# Reverse a single Linked List

```python
def rev_link_list(head):
    prev = None
    curr = head
    while curr:
        next_ = curr.next
        curr.next = prev
        prev = curr
        curr = next_
    return prev
```
This is runs on O(n) and space O(1)

# There is also a recursive Method