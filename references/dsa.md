# DSA Reference -- Data Structures and Algorithms

## Core Data Structures

### Arrays and Strings
- Most common interview structure. Know two-pointer, sliding window, prefix sum.
- Prefix sum: precompute cumulative sums to answer range queries in O(1)
- Kadane's algorithm: maximum subarray sum in O(n)

### Linked Lists
- Singly vs Doubly vs Circular
- Key operations: reverse, detect cycle (Floyd's), find middle (slow/fast pointer), merge two sorted lists
- Dummy node trick avoids edge cases for head deletion

### Stacks and Queues
- Stack: LIFO. Use for: balanced parentheses, next greater element, infix to postfix, undo operations
- Queue: FIFO. Use for: BFS, sliding window maximum (deque), task scheduling
- Monotonic stack: maintains increasing or decreasing order, useful for span/histogram problems

### Trees
- Binary Tree vs BST vs AVL vs Red-Black Tree
- BST property: left < root < right. Inorder traversal of BST gives sorted array.
- Tree traversals: Inorder (LNR), Preorder (NLR), Postorder (LRN), Level Order (BFS)
- Height of tree: max depth from root to leaf
- Balanced tree: |height(left) minus height(right)| <= 1 for all nodes

### Heaps
- Max-Heap: parent >= children. Min-Heap: parent <= children.
- Used for: top-K elements, merge K sorted lists, median in a stream
- Heapify: O(n). Insert/Delete: O(log n). Peek: O(1)
- Python: heapq is a min-heap. Negate values for max-heap.

### Hash Maps and Hash Sets
- Average O(1) for get, put, delete
- Collision resolution: chaining (linked list), open addressing (linear probing)
- Use for: frequency counting, two-sum, anagram detection, caching

### Graphs
- Representations: Adjacency Matrix (O(V^2) space), Adjacency List (O(V+E) space)
- BFS: level-by-level, uses a queue, shortest path in unweighted graphs
- DFS: depth-first, uses a stack or recursion, detects cycles, topological sort
- Topological Sort: for DAGs, ordering of tasks with dependencies (Kahn's or DFS)
- Dijkstra: shortest path in weighted graphs with non-negative weights, O((V+E) log V)
- Bellman-Ford: handles negative weights, O(VE)
- Union-Find: detect cycles, Kruskal's MST
- Kruskal vs Prim: both for MST. Kruskal sorts edges, Prim grows from a node.

### Tries
- Prefix tree for strings. Insert and search in O(L) where L is word length
- Used for: autocomplete, word search, prefix matching

---

## Algorithm Patterns

### Sliding Window
Use when: subarray/substring problems with a size or condition constraint
Template:
```python
left = 0
for right in range(len(arr)):
    # expand window: add arr[right]
    while window_condition_violated:
        # shrink window: remove arr[left]
        left += 1
    # update answer
```

### Binary Search
Use when: sorted array or a search space with a monotonic property
```python
lo, hi = 0, len(arr) - 1
while lo <= hi:
    mid = (lo + hi) // 2
    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        lo = mid + 1
    else:
        hi = mid - 1
return -1
```
Binary search on answer: "find minimum X such that condition(X) is True"

### Dynamic Programming
Two signals: optimal substructure + overlapping subproblems
Steps:
1. Define dp[i] clearly in words
2. Write the recurrence relation
3. Identify base cases
4. Decide top-down (memoization) or bottom-up (tabulation)

Classic DP problems:
- Fibonacci, Climbing Stairs (1D DP)
- Longest Common Subsequence (2D DP)
- 0/1 Knapsack (2D DP)
- Coin Change (1D DP, unbounded)
- Longest Increasing Subsequence (O(n^2) DP or O(n log n) with patience sorting)
- Edit Distance (2D DP)

### Backtracking
Use when: generating all combinations, permutations, or valid configurations
```python
def backtrack(state):
    if is_complete(state):
        results.append(state[:])
        return
    for choice in get_choices(state):
        make_choice(state, choice)
        backtrack(state)
        undo_choice(state, choice)
```

### Greedy
Use when: locally optimal choices lead to globally optimal solution
Examples: Activity Selection, Huffman Coding, Minimum number of platforms

---

## Top 50 Must-Solve Problems

**Arrays**
1. Two Sum
2. Best Time to Buy and Sell Stock
3. Maximum Subarray (Kadane's)
4. Product of Array Except Self
5. Container With Most Water
6. Merge Intervals
7. Find the Duplicate Number
8. Trapping Rain Water

**Binary Search**
9. Search in Rotated Sorted Array
10. Find Minimum in Rotated Sorted Array
11. Koko Eating Bananas (binary search on answer)

**Linked Lists**
12. Reverse a Linked List
13. Detect Cycle in Linked List
14. Merge Two Sorted Lists
15. Find Middle of Linked List
16. LRU Cache

**Trees**
17. Inorder, Preorder, Postorder Traversal
18. Maximum Depth of Binary Tree
19. Validate BST
20. Lowest Common Ancestor
21. Diameter of Binary Tree
22. Level Order Traversal
23. Serialize and Deserialize Binary Tree

**Graphs**
24. Number of Islands (BFS/DFS)
25. Clone Graph
26. Course Schedule (Topological Sort)
27. Word Ladder
28. Dijkstra Shortest Path
29. Detect Cycle in Directed and Undirected Graph

**DP**
30. Climbing Stairs
31. House Robber
32. Longest Common Subsequence
33. 0/1 Knapsack
34. Coin Change
35. Longest Increasing Subsequence
36. Edit Distance
37. Partition Equal Subset Sum
38. Word Break

**Heaps and Priority Queues**
39. Kth Largest Element in an Array
40. Top K Frequent Elements
41. Merge K Sorted Lists
42. Median from Data Stream

**Strings**
43. Valid Anagram
44. Longest Substring Without Repeating Characters
45. Longest Palindromic Substring
46. Group Anagrams
47. Minimum Window Substring

**Backtracking**
48. Subsets
49. Permutations
50. N-Queens

---

## Complexity Cheat Sheet

| Algorithm | Best | Average | Worst | Space |
|---|---|---|---|---|
| Bubble Sort | O(n) | O(n^2) | O(n^2) | O(1) |
| Selection Sort | O(n^2) | O(n^2) | O(n^2) | O(1) |
| Insertion Sort | O(n) | O(n^2) | O(n^2) | O(1) |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) |
| Quick Sort | O(n log n) | O(n log n) | O(n^2) | O(log n) |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) |
| Binary Search | O(1) | O(log n) | O(log n) | O(1) |
| BFS / DFS | O(V+E) | O(V+E) | O(V+E) | O(V) |
| Dijkstra | O(E) | O((V+E) log V) | O((V+E) log V) | O(V) |
