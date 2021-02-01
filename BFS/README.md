# Breadth First Search
## Solved Problems
- Type 1:
  - level order traversal
  - exercises:

- Type 2:
  - shortest path for uniform path
  - exercises:
  
## Data Structures in BFS
  - Queue or Heap
  - HashSet
 
## Coding Format:

```java
Queue<E> queue = new ArrayDeque<>();
Set<E> visited = new HashSet<>();

queue.offer(E);
visited.add(E);
int step = 0;

while (!queue.isEmpty()) {
    int size = queue.size();
	  for (int i = 0; i < size; i ++) {
	          E e = queue.poll();

            if (e = target) {
                return step;
            }

            for (E e : neighbors) {
                if (!visited.contains(e)) {
                     queue.offer(e);
                     visited.add(e);
                 }
             }
     }
     step++;
}
```

end.
