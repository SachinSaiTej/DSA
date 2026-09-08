# DSA Interview Prep

A Java-focused DSA interview revision guide organized by problem pattern.

## Structure

Each topic has its own directory with a topic index. Each problem has its own Markdown file containing:

- Problem statement
- Example
- Intuition
- Optimal approach
- Optimal Java code
- Time and space complexity
- Interview notes / pitfalls

## Topics

| # | Topic | Questions |
|---:|---|---:|
| 1 | [Arrays](./DSA-Prep/01-Arrays/README.md) | 17 |
| 2 | [Strings](./DSA-Prep/02-Strings/README.md) | 12 |
| 3 | [HashMap / HashSet](./DSA-Prep/03-HashMap-HashSet/README.md) | 15 |
| 4 | [Two Pointers](./DSA-Prep/04-Two-Pointers/README.md) | 13 |
| 5 | [Sliding Window](./DSA-Prep/05-Sliding-Window/README.md) | 12 |
| 6 | [Prefix Sum](./DSA-Prep/06-Prefix-Sum/README.md) | 10 |
| 7 | [Sorting](./DSA-Prep/07-Sorting/README.md) | 10 |
| 8 | [Binary Search](./DSA-Prep/08-Binary-Search/README.md) | 12 |
| 9 | [Linked List](./DSA-Prep/09-Linked-List/README.md) | 15 |
| 10 | [Stack](./DSA-Prep/10-Stack/README.md) | 12 |
| 11 | [Queue / Deque](./DSA-Prep/11-Queue-Deque/README.md) | 7 |
| 12 | [Recursion](./DSA-Prep/12-Recursion/README.md) | 7 |
| 13 | [Binary Tree](./DSA-Prep/13-Binary-Tree/README.md) | 15 |
| 14 | [Binary Search Tree](./DSA-Prep/14-BST/README.md) | 8 |
| 15 | [Heap / Priority Queue](./DSA-Prep/15-Heap-PriorityQueue/README.md) | 10 |
| 16 | [Greedy](./DSA-Prep/16-Greedy/README.md) | 13 |
| 17 | [Graph BFS / DFS](./DSA-Prep/17-Graph-BFS-DFS/README.md) | 9 |
| 18 | [Topological Sort](./DSA-Prep/18-Topological-Sort/README.md) | 6 |
| 19 | [Shortest Path](./DSA-Prep/19-Shortest-Path/README.md) | 7 |
| 20 | [Union Find](./DSA-Prep/20-Union-Find/README.md) | 7 |
| 21 | [Dynamic Programming](./DSA-Prep/21-Dynamic-Programming/README.md) | 12 |
| 22 | [Bit Manipulation](./DSA-Prep/22-Bit-Manipulation/README.md) | 9 |
| 23 | [Matrix](./DSA-Prep/23-Matrix/README.md) | 10 |
| 24 | [Intervals](./DSA-Prep/24-Intervals/README.md) | 9 |
| 25 | [Trie](./DSA-Prep/25-Trie/README.md) | 6 |
| 26 | [Segment Tree](./DSA-Prep/26-Segment-Tree/README.md) | 6 |
| 27 | [Backtracking](./DSA-Prep/27-Backtracking/README.md) | 14 |

**281 question entries** across the full revision list. Some problems intentionally appear in multiple topics because they represent multiple interview patterns.

## Revision Workflow

1. Identify the pattern before coding.
2. Recall the invariant / key insight.
3. Write the optimal solution.
4. State time and space complexity.
5. Check edge cases and Java-specific pitfalls.

## Java DSA Quick Reference

- `Integer.MIN_VALUE`, `Integer.MAX_VALUE`
- `Math.abs`, `Math.max`, `Math.min`
- `Arrays.sort`, `Arrays.fill`
- `HashMap`, `HashSet`
- `ArrayList`, `Deque`, `PriorityQueue`
- `StringBuilder`
- `long` for overflow-sensitive sums/products
- `left + (right - left) / 2` for binary search
