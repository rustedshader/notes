# Shortest Path to a point using graphs

For Solving my Graph Theory problems on Grids


```python
from collections import deque

def solve(start_x, start_y, dest_x, dest_y):
    # Here i am checking if it can keep on drift in same direction then just return 0
    if start_x == dest_x:
        return 0
    if start_y == dest_y:
        return 0
    queue = deque()
    queue.append(((start_x, start_y), 0))
    visited = set()
    visited.add((start_x, start_y))
    
    # Normal BFS
    while queue:
        node, count = queue.popleft()
        x, y = node

        if node == (dest_x, dest_y):
            # I did this because N is the the number of steps but drifts between steps is -1
            return count - 1
        
        # Normal BFS to all 4 possiblities in graph of N S W E
        for dx, dy in [(-1, 0), (1, 0), (0, -1), (0, 1)]:
            nx, ny = x + dx, y + dy
            if 0 <= nx <= 1000 and 0 <= ny <= 1000 and (nx, ny) not in visited:
                visited.add((nx, ny))
                queue.append(((nx, ny), count + 1))

    return -1  


N = int(input())
intitial_x,initial_y = map(int,input().split(" "))
dest_x,dest_y = map(int,input().split(" "))


print(solve(intitial_x, initial_y, dest_x, dest_y)) 
```