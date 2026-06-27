# Advanced Data Structures & Algorithms Handbook (Java)

> A complete advanced-level handbook for mastering Data Structures and Algorithms with Java syntax, logic, examples, code walkthroughs, concept differences, practice tasks, and interview preparation.

---

## Table of Contents

1. Foundations: Complexity, Recursion, and Math
2. Arrays and Strings
3. Linked Lists
4. Stacks and Queues
5. Hashing and Hash Tables
6. Trees (Binary Tree, BST, Balanced Trees)
7. Heaps and Priority Queues
8. Tries
9. Graphs
10. Greedy Algorithms
11. Divide and Conquer
12. Dynamic Programming
13. Backtracking and Branch & Bound
14. Bit Manipulation
15. Sliding Window, Two Pointers, and Prefix Techniques
16. Advanced DS: Union-Find, Segment Tree, Fenwick Tree
17. Differences Between Major Data Structures (Detailed)
18. Interview Questions and Answers (Google/Amazon/Product Companies)

---

## 1) Foundations: Complexity, Recursion, and Math

### 1.1 Time and Space Complexity

Complexity analysis estimates resource usage as input size `n` grows.

- **Time Complexity**: number of operations.
- **Space Complexity**: extra memory usage.

Common orders:
- `O(1)` constant
- `O(log n)` logarithmic
- `O(n)` linear
- `O(n log n)` linearithmic
- `O(n^2)` quadratic
- `O(2^n)` exponential

#### Java Example

```java
public class ComplexityDemo {
    // O(n)
    public static int sum(int[] arr) {
        int s = 0;
        for (int x : arr) s += x;
        return s;
    }

    // O(log n)
    public static int binarySearch(int[] arr, int target) {
        int l = 0, r = arr.length - 1;
        while (l <= r) {
            int m = l + (r - l) / 2;
            if (arr[m] == target) return m;
            if (arr[m] < target) l = m + 1;
            else r = m - 1;
        }
        return -1;
    }
}
```

**How this works:**
- `sum` scans every element once ⇒ `O(n)`.
- `binarySearch` discards half each iteration ⇒ `O(log n)`.

**Practice task:**
Analyze the time and space complexity of merge sort, quick sort (average and worst), and BFS.

---

### 1.2 Recursion and Recurrence

Recursion solves a problem using smaller subproblems.

#### Java Example: Factorial

```java
public static long fact(int n) {
    if (n <= 1) return 1;
    return n * fact(n - 1);
}
```

**How this works:**
- Base case: `n <= 1`.
- Recursive case: multiply `n` by factorial of `n-1`.
- Stack depth: `O(n)`.

**Practice task:**
Write recursive and iterative Fibonacci. Compare runtime and memory.

---

## 2) Arrays and Strings

### 2.1 Arrays

Contiguous memory, index-based access.

- Access: `O(1)`
- Insert/delete at end (dynamic array): amortized `O(1)`
- Insert/delete middle: `O(n)`

#### Java Example: Reverse Array

```java
public static void reverse(int[] a) {
    int l = 0, r = a.length - 1;
    while (l < r) {
        int t = a[l];
        a[l] = a[r];
        a[r] = t;
        l++; r--;
    }
}
```

**How this works:**
- Swap symmetric elements from both ends.
- Runs `n/2` swaps ⇒ `O(n)` time, `O(1)` extra space.

**Practice task:**
Implement rotate array by `k` using reversal method.

---

### 2.2 Strings

In Java, `String` is immutable. Use `StringBuilder` for efficient modifications.

#### Java Example: Palindrome Check

```java
public static boolean isPalindrome(String s) {
    int l = 0, r = s.length() - 1;
    while (l < r) {
        if (s.charAt(l) != s.charAt(r)) return false;
        l++; r--;
    }
    return true;
}
```

**How this works:**
- Compare mirrored characters.
- First mismatch ⇒ not palindrome.

**Practice task:**
Find longest common prefix in array of strings.

---

## 3) Linked Lists

Node-based linear structure.

Types:
- Singly Linked List
- Doubly Linked List
- Circular Linked List

#### Java Node and Reverse List

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int v) { val = v; }
}

public static ListNode reverseList(ListNode head) {
    ListNode prev = null, cur = head;
    while (cur != null) {
        ListNode nxt = cur.next;
        cur.next = prev;
        prev = cur;
        cur = nxt;
    }
    return prev;
}
```

**How this works:**
- Rewire each node’s `next` to previous node.
- Maintain `prev`, `cur`, `nxt` to avoid losing the rest of list.

**Practice task:**
Detect cycle in linked list using Floyd’s slow-fast pointer algorithm.

---

## 4) Stacks and Queues

### 4.1 Stack (LIFO)

Use cases: expression evaluation, recursion simulation, monotonic stack.

#### Java Example: Valid Parentheses

```java
import java.util.*;

public static boolean isValid(String s) {
    Deque<Character> st = new ArrayDeque<>();
    for (char c : s.toCharArray()) {
        if (c == '(' || c == '{' || c == '[') st.push(c);
        else {
            if (st.isEmpty()) return false;
            char t = st.pop();
            if ((c == ')' && t != '(') ||
                (c == '}' && t != '{') ||
                (c == ']' && t != '[')) return false;
        }
    }
    return st.isEmpty();
}
```

**How this works:**
- Push opening brackets.
- On closing, top must match type.
- End with empty stack for valid sequence.

**Practice task:**
Implement MinStack with `getMin()` in `O(1)`.

---

### 4.2 Queue (FIFO)

Use cases: BFS, scheduling, buffering.

#### Java Example: Basic Queue Usage

```java
Queue<Integer> q = new ArrayDeque<>();
q.offer(10);
q.offer(20);
int front = q.poll(); // 10
```

**Practice task:**
Implement queue using two stacks.

---

## 5) Hashing and Hash Tables

Hash map gives near O(1) average lookup/insert/delete.

- Collision handling: chaining/open addressing.
- Java uses bucket arrays + tree bins (in some collision-heavy cases).

#### Java Example: Two Sum

```java
import java.util.*;

public static int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int need = target - nums[i];
        if (map.containsKey(need)) return new int[]{map.get(need), i};
        map.put(nums[i], i);
    }
    return new int[]{-1, -1};
}
```

**How this works:**
- For each value, check if complement was seen earlier.
- One pass ⇒ `O(n)` average.

**Practice task:**
Group anagrams efficiently using hash-based signatures.

---

## 6) Trees (Binary Tree, BST, Balanced Trees)

### 6.1 Binary Tree Traversals

DFS traversals:
- Preorder: Root-Left-Right
- Inorder: Left-Root-Right
- Postorder: Left-Right-Root

#### Java Example: Inorder

```java
class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int v) { val = v; }
}

public static void inorder(TreeNode root) {
    if (root == null) return;
    inorder(root.left);
    System.out.print(root.val + " ");
    inorder(root.right);
}
```

**Practice task:**
Write iterative inorder traversal using stack.

---

### 6.2 Binary Search Tree (BST)

Property: left < root < right.

Operations average `O(log n)`, worst `O(n)` if skewed.

#### Java Example: Search in BST

```java
public static TreeNode searchBST(TreeNode root, int key) {
    while (root != null && root.val != key) {
        root = key < root.val ? root.left : root.right;
    }
    return root;
}
```

**Practice task:**
Implement insert and delete in BST with all 3 delete cases.

---

### 6.3 Balanced BST (AVL/Red-Black)

Self-balancing keeps height `O(log n)`.

- **AVL**: stricter balance, faster lookups.
- **Red-Black**: fewer rotations on updates.

**Practice task:**
Explain LL, RR, LR, RL rotations with diagrams and code skeleton.

---

## 7) Heaps and Priority Queues

Heap is a complete binary tree with heap-order property.

- Min-heap: parent <= children
- Max-heap: parent >= children

#### Java Example: Kth Largest

```java
import java.util.*;

public static int findKthLargest(int[] nums, int k) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    for (int x : nums) {
        minHeap.offer(x);
        if (minHeap.size() > k) minHeap.poll();
    }
    return minHeap.peek();
}
```

**How this works:**
- Maintain k largest seen so far.
- Heap top becomes kth largest.

**Practice task:**
Merge k sorted arrays using min-heap.

---

## 8) Tries

Trie stores strings by characters for prefix operations.

#### Java Example: Trie Insert + Search

```java
class TrieNode {
    TrieNode[] ch = new TrieNode[26];
    boolean end;
}

class Trie {
    TrieNode root = new TrieNode();

    void insert(String s) {
        TrieNode cur = root;
        for (char c : s.toCharArray()) {
            int i = c - 'a';
            if (cur.ch[i] == null) cur.ch[i] = new TrieNode();
            cur = cur.ch[i];
        }
        cur.end = true;
    }

    boolean search(String s) {
        TrieNode cur = root;
        for (char c : s.toCharArray()) {
            int i = c - 'a';
            if (cur.ch[i] == null) return false;
            cur = cur.ch[i];
        }
        return cur.end;
    }
}
```

**Practice task:**
Add `startsWith(prefix)` and delete-word operation.

---

## 9) Graphs

Representations:
- Adjacency List (`O(V+E)` space)
- Adjacency Matrix (`O(V^2)` space)

### 9.1 BFS and DFS

#### Java Example: BFS

```java
import java.util.*;

public static List<Integer> bfs(int n, List<List<Integer>> g, int src) {
    boolean[] vis = new boolean[n];
    Queue<Integer> q = new ArrayDeque<>();
    List<Integer> order = new ArrayList<>();
    q.offer(src);
    vis[src] = true;

    while (!q.isEmpty()) {
        int u = q.poll();
        order.add(u);
        for (int v : g.get(u)) {
            if (!vis[v]) {
                vis[v] = true;
                q.offer(v);
            }
        }
    }
    return order;
}
```

**Practice task:**
Find shortest path in unweighted graph from source to all nodes.

---

### 9.2 Dijkstra (Non-negative Weights)

Use priority queue to greedily relax nearest node.

**Practice task:**
Implement Dijkstra with parent array to reconstruct shortest path.

---

### 9.3 Topological Sort

For DAG dependency ordering.

- Kahn’s algorithm (BFS indegree)
- DFS finishing order

**Practice task:**
Detect cycle in directed graph and return valid topological order if acyclic.

---

## 10) Greedy Algorithms

Greedy picks locally optimal decision hoping global optimum.

Works when:
- Greedy-choice property
- Optimal substructure

Examples: activity selection, Huffman coding, interval merge-like tasks.

**Practice task:**
Given intervals, remove minimum to make non-overlapping.

---

## 11) Divide and Conquer

Divide problem into smaller independent subproblems, solve recursively, combine.

Examples:
- Merge Sort
- Quick Sort
- Binary Search

#### Java Example: Merge Sort

```java
public static void mergeSort(int[] a, int l, int r) {
    if (l >= r) return;
    int m = l + (r - l) / 2;
    mergeSort(a, l, m);
    mergeSort(a, m + 1, r);
    merge(a, l, m, r);
}

private static void merge(int[] a, int l, int m, int r) {
    int[] tmp = new int[r - l + 1];
    int i = l, j = m + 1, k = 0;
    while (i <= m && j <= r) tmp[k++] = (a[i] <= a[j]) ? a[i++] : a[j++];
    while (i <= m) tmp[k++] = a[i++];
    while (j <= r) tmp[k++] = a[j++];
    for (int t = 0; t < tmp.length; t++) a[l + t] = tmp[t];
}
```

**Practice task:**
Count inversions using merge-sort based approach.

---

## 12) Dynamic Programming (DP)

DP = optimize recursion by storing overlapping subproblem results.

Styles:
- Top-down (memoization)
- Bottom-up (tabulation)

#### Java Example: 0/1 Knapsack (Tabulation)

```java
public static int knapsack(int[] wt, int[] val, int W) {
    int n = wt.length;
    int[][] dp = new int[n + 1][W + 1];

    for (int i = 1; i <= n; i++) {
        for (int w = 0; w <= W; w++) {
            dp[i][w] = dp[i - 1][w];
            if (wt[i - 1] <= w) {
                dp[i][w] = Math.max(dp[i][w], val[i - 1] + dp[i - 1][w - wt[i - 1]]);
            }
        }
    }
    return dp[n][W];
}
```

**How this works:**
- `dp[i][w]` = best value using first `i` items and capacity `w`.
- Transition: skip item OR take item (if fits).

**Practice task:**
Solve Longest Increasing Subsequence in `O(n log n)`.

---

## 13) Backtracking and Branch & Bound

Backtracking explores decision tree, undoing choices when invalid/unpromising.

#### Java Example: N-Queens (Core)

```java
public static void solveNQueens(int row, int n, char[][] board,
                                boolean[] col, boolean[] d1, boolean[] d2,
                                List<List<String>> ans) {
    if (row == n) {
        List<String> sol = new ArrayList<>();
        for (char[] r : board) sol.add(new String(r));
        ans.add(sol);
        return;
    }
    for (int c = 0; c < n; c++) {
        int id1 = row - c + n, id2 = row + c;
        if (col[c] || d1[id1] || d2[id2]) continue;
        col[c] = d1[id1] = d2[id2] = true;
        board[row][c] = 'Q';
        solveNQueens(row + 1, n, board, col, d1, d2, ans);
        board[row][c] = '.';
        col[c] = d1[id1] = d2[id2] = false;
    }
}
```

**Practice task:**
Implement Sudoku solver using constraint checks.

---

## 14) Bit Manipulation

Useful for compact states, subsets, parity, masks.

Core operations:
- Set bit: `x | (1 << k)`
- Clear bit: `x & ~(1 << k)`
- Toggle bit: `x ^ (1 << k)`
- Check bit: `(x & (1 << k)) != 0`

#### Java Example: Count Set Bits

```java
public static int popcount(int x) {
    int c = 0;
    while (x != 0) {
        x &= (x - 1);
        c++;
    }
    return c;
}
```

**How this works:**
- `x & (x-1)` removes the lowest set bit each iteration.
- Loops number of 1s times.

**Practice task:**
Generate all subsets of an array using bit masks.

---

## 15) Sliding Window, Two Pointers, Prefix Techniques

### 15.1 Sliding Window

For contiguous subarray/substring constraints.

#### Java Example: Longest Substring Without Repeating Characters

```java
import java.util.*;

public static int lengthOfLongestSubstring(String s) {
    Map<Character, Integer> last = new HashMap<>();
    int l = 0, ans = 0;
    for (int r = 0; r < s.length(); r++) {
        char c = s.charAt(r);
        if (last.containsKey(c)) l = Math.max(l, last.get(c) + 1);
        last.put(c, r);
        ans = Math.max(ans, r - l + 1);
    }
    return ans;
}
```

**Practice task:**
Find minimum window substring containing all chars of target.

---

### 15.2 Prefix Sum

Precompute cumulative sums for range query optimization.

**Practice task:**
Number of subarrays with sum `k` using prefix hash map.

---

## 16) Advanced DS: Union-Find, Segment Tree, Fenwick Tree

### 16.1 Union-Find (Disjoint Set Union)

Operations:
- `find(x)` representative
- `union(a, b)` merge sets

Optimizations:
- Path compression
- Union by rank/size

#### Java Example

```java
class DSU {
    int[] p, r;
    DSU(int n) {
        p = new int[n]; r = new int[n];
        for (int i = 0; i < n; i++) p[i] = i;
    }
    int find(int x) {
        if (p[x] != x) p[x] = find(p[x]);
        return p[x];
    }
    void union(int a, int b) {
        int pa = find(a), pb = find(b);
        if (pa == pb) return;
        if (r[pa] < r[pb]) p[pa] = pb;
        else if (r[pa] > r[pb]) p[pb] = pa;
        else { p[pb] = pa; r[pa]++; }
    }
}
```

**Practice task:**
Use DSU to detect cycle in an undirected graph.

---

### 16.2 Segment Tree

Supports range query + point/range updates efficiently (`O(log n)`).

Use cases: range sum/min/max, lazy propagation.

**Practice task:**
Implement segment tree for range minimum query with point update.

---

### 16.3 Fenwick Tree (Binary Indexed Tree)

Efficient prefix sums and updates in `O(log n)` with simpler memory than segment tree.

**Practice task:**
Implement BIT and solve inversion count.

---

## 17) Detailed Differences Between Major Data Structures

### 17.1 Array vs Linked List

- **Memory**: Array contiguous; Linked list non-contiguous nodes.
- **Access**: Array random access `O(1)`; Linked list access `O(n)`.
- **Insert/Delete middle**: Array `O(n)` shifts; Linked list `O(1)` if node reference known.
- **Cache performance**: Array better due to locality.

### 17.2 Stack vs Queue

- Stack LIFO; Queue FIFO.
- Stack used in DFS, undo, parsing.
- Queue used in BFS, scheduling, buffering.

### 17.3 HashMap vs TreeMap (Java)

- HashMap average `O(1)` operations, unordered.
- TreeMap `O(log n)` ordered keys (Red-Black Tree).

### 17.4 BST vs Heap

- BST supports ordered search/range queries.
- Heap gives fast min/max retrieval (`peek`), not full ordering.

### 17.5 Trie vs HashMap for Strings

- Trie efficient prefix queries.
- HashMap better simple exact key lookup with less pointer overhead generally.

### 17.6 Segment Tree vs Fenwick Tree

- Fenwick simpler, smaller, great for prefix-sum-like ops.
- Segment tree more flexible (min/max/gcd/range updates with lazy).

### 17.7 Graph (Matrix vs List)

- Matrix: `O(1)` edge check, high memory `O(V^2)`.
- List: memory `O(V+E)`, better for sparse graphs.

**Practice task:**
Create a comparison table for all above with: operation complexities, memory, best use-case, interview pattern.

---

## 18) Interview Questions and Answers (Google/Amazon/Product Companies)

> These are representative high-frequency patterns asked across product companies.

### Q1. Why is HashMap lookup O(1) average but O(n) worst case?
**Answer:**
Average O(1) assumes good hash distribution and low collision load. Worst case occurs when many keys map to same bucket, degrading to linear scan/tree traversal depending on implementation.

### Q2. When do you choose BFS over DFS?
**Answer:**
Use BFS when shortest path in unweighted graph is needed or when level-order behavior matters. DFS is preferred for exhaustive traversal, cycle detection variants, topological DFS, and backtracking.

### Q3. Explain memoization vs tabulation.
**Answer:**
Memoization is top-down recursion + cache, computing only needed states. Tabulation is bottom-up iterative filling over all states in dependency order. Tabulation avoids recursion stack overhead.

### Q4. Why can quicksort become O(n^2)?
**Answer:**
Poor pivot consistently creates highly unbalanced partitions (e.g., sorted input with naive pivot). Randomized pivot or median-of-three mitigates this.

### Q5. Difference between process and thread? (Often in system design rounds)
**Answer:**
Process has isolated memory space; thread shares process memory. Threads are lighter context switches but require synchronization for shared data.

### Q6. How would you detect a cycle in directed graph?
**Answer:**
Use DFS with recursion stack (colors/visited+pathVisited) or Kahn’s algorithm: if topological order size < V, cycle exists.

### Q7. Explain CAP in context of distributed key-value store.
**Answer:**
Under network partition, you choose consistency or availability tradeoff. Practical systems choose tunable or scenario-dependent balance.

### Q8. How does LRU cache work in O(1)?
**Answer:**
HashMap for key→node lookup + doubly linked list for recency order. On access/update: move node to front. On eviction: remove tail.

### Q9. When to use Trie in interviews?
**Answer:**
Whenever prefix search, autocomplete, dictionary matching, wildcard prefix, or word-break optimization with prefix constraints appears.

### Q10. How to optimize Dijkstra for dense vs sparse graphs?
**Answer:**
Sparse: adjacency list + min-heap (`O((V+E)logV)`). Dense: adjacency matrix + array-based min selection can be competitive (`O(V^2)`).

### Q11. Explain monotonic stack use cases.
**Answer:**
Nearest greater/smaller element, stock span, histogram largest rectangle, rain water variants. Maintains ordered stack to avoid re-scanning.

### Q12. Why does union-find become nearly O(1)?
**Answer:**
Path compression + union by rank gives inverse Ackermann complexity `α(n)`, practically constant.

### Q13. Design a rate limiter.
**Answer:**
Common approaches: token bucket, leaky bucket, fixed window, sliding window log/counter. Choose based on burst handling and precision vs storage.

### Q14. Explain eventual consistency with example.
**Answer:**
Replicas may temporarily diverge but converge later. Example: social feed likes count may lag but eventually synchronize.

### Q15. How to approach a coding interview problem?
**Answer:**
Clarify constraints → brute force → optimize with data structure/pattern → analyze complexity → write clean code → test edge cases.

---

## Suggested 8-Week Practice Roadmap

- **Week 1:** Complexity, arrays, strings, two pointers
- **Week 2:** Linked list, stack, queue, hashing
- **Week 3:** Trees, BST, heaps, trie
- **Week 4:** Graph traversal, shortest paths, topo sort
- **Week 5:** Recursion, backtracking, divide & conquer
- **Week 6:** DP basics to advanced patterns
- **Week 7:** Advanced DS (DSU, segment tree, BIT)
- **Week 8:** Mixed interview sets + timed mocks

Daily routine:
1. 1 concept revision (30–45 mins)
2. 2 medium + 1 hard problem (2–3 hrs)
3. Post-solve complexity writeup (15 mins)
4. Re-solve missed problem after 48 hrs

---

## Final Notes

- Master **patterns**, not just questions.
- Always articulate: constraints, invariant, complexity, edge cases.
- In interviews, communication quality matters as much as correctness.

Good luck — with consistent practice and revision cycles, this handbook can significantly boost your product-company interview readiness.
