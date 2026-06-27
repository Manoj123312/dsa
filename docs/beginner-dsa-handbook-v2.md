# Beginner Data Structures & Algorithms Handbook (Version 3)

A complete **beginner-level** and **interview-focused** handbook for Data Structures and Algorithms in Java.

This version includes, for every concept:
1. Definition  
2. Use  
3. When & why it is used  
4. Syntax and logic  
5. Time and Space Complexity (best case and worst case + why)  
6. Basic Java example with detailed explanation  
7. Small hands-on task  

Also included:
- Detailed explanation of Time Complexity and Space Complexity
- Detailed differences between data structures
- Interview questions with answers asked in Google, Amazon, and other product companies

---

## Table of Contents

1. Introduction to DSA  
2. Time Complexity and Space Complexity (Detailed)  
3. Arrays  
4. Strings  
5. Linked Lists  
6. Stack  
7. Queue  
8. Hashing (HashMap / HashSet)  
9. Trees  
10. Binary Search Tree (BST)  
11. Heap / Priority Queue  
12. Trie  
13. Graphs  
14. Sorting Algorithms  
15. Searching Algorithms  
16. Recursion  
17. Dynamic Programming (DP)  
18. Greedy Algorithms  
19. Backtracking  
20. Sliding Window and Two Pointers  
21. Detailed Differences Between Data Structures  
22. Interview Questions with Answers  
23. Beginner Practice Roadmap  

---

## 1) Introduction to DSA

### Definition
- **Data Structure**: A way to store and organize data efficiently.
- **Algorithm**: A step-by-step procedure to solve a problem.

### Use
- Improves performance of code.
- Helps solve real-world and interview problems systematically.

### When & Why Used
- Used in almost every software system (apps, websites, search engines, payment systems).
- Right choice of data structure + algorithm = faster and scalable systems.

### Syntax and Logic
No direct syntax. DSA is a concept layer over programming.

### Example (Java)
```java
int[] nums = {4, 9, 2, 7};

// Algorithm: find maximum
int max = nums[0];
for (int i = 1; i < nums.length; i++) {
    if (nums[i] > max) max = nums[i];
}
System.out.println(max); // 9
```

### Explanation
- Array stores data.
- Loop compares and updates max.

### Complexity
- Time: O(n)
- Space: O(1)

### Practice Task
Find minimum and maximum in one pass.

---

## 2) Time Complexity and Space Complexity (Detailed)

## 2.1 Time Complexity

### Definition
Time complexity tells how the runtime grows with input size `n`.

### Use
- Compare algorithms.
- Choose faster approach for large data.

### When & Why Used
- During optimization and interviews.
- To predict performance before deploying code.

### Common Orders
- **O(1)**: Constant time (independent of n)
- **O(log n)**: Logarithmic (input halves repeatedly)
- **O(n)**: Linear
- **O(n log n)**: Efficient sorting class
- **O(n²)**: Nested loops over n
- **O(2^n), O(n!)**: Exponential/factorial (very expensive)

### Best Case vs Worst Case
- **Best case**: Most favorable input.
- **Worst case**: Most difficult input.
- Worst-case is usually used in interviews because it guarantees upper bound.

### Example
```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) return i;
    }
    return -1;
}
```
- Best case: O(1) (target at first index)
- Worst case: O(n) (target last or absent)

---

## 2.2 Space Complexity

### Definition
Space complexity is the extra memory used by an algorithm as input grows.

### Use
- Important in memory-constrained systems.
- Helps avoid memory overflow and improve efficiency.

### When & Why Used
- Used when handling large inputs.
- Required in interviews to compare optimized solutions.

### Includes
- Auxiliary memory (extra arrays, stacks, maps)
- Recursion call stack

### Example
```java
public static int[] copyArray(int[] arr) {
    int[] copy = new int[arr.length];
    for (int i = 0; i < arr.length; i++) {
        copy[i] = arr[i];
    }
    return copy;
}
```
- Time: O(n)
- Extra space: O(n) (new array)

### Practice Task
Compare recursive Fibonacci vs iterative Fibonacci for time and space.

---

## 3) Arrays

### Definition
Array stores same-type elements in contiguous memory.

### Use
- Fast index access
- Useful for fixed-size or near-fixed-size data

### When & Why Used
- Use when random access is needed.
- Very common base for other structures.

### Syntax and Logic
```java
int[] arr = {10, 20, 30};
int x = arr[1]; // 20
```

### Complexity (Array Operations)
- Access by index: Best O(1), Worst O(1)
- Search unsorted: Best O(1), Worst O(n)
- Insert at end (space available): Best O(1), Worst O(1)
- Insert at middle: Best O(1) (at end-like position), Worst O(n) due to shifts
- Delete at middle: Worst O(n)

### Example
```java
public static int secondLargest(int[] arr) {
    int first = Integer.MIN_VALUE, second = Integer.MIN_VALUE;
    for (int num : arr) {
        if (num > first) {
            second = first;
            first = num;
        } else if (num > second && num != first) {
            second = num;
        }
    }
    return second;
}
```

### Explanation
- Track top two values in one pass.
- Efficient and no sorting required.

### Complexity
- Time: O(n)
- Space: O(1)

### Practice Task
Rotate array by `k` steps to right.

---

## 4) Strings

### Definition
String is a sequence of characters.

### Use
- Text processing, validation, formatting, parsing.

### When & Why Used
- Any input/output text operation.

### Syntax and Logic
```java
String s = "hello";
StringBuilder sb = new StringBuilder(s);
sb.append(" world");
```
- `String` is immutable.
- `StringBuilder` is mutable and efficient for repeated changes.

### Complexity
- Access char by index: O(1)
- Concatenation with `+` in loop: can be costly
- Using StringBuilder append: amortized efficient

### Example
```java
public static boolean isPalindrome(String s) {
    int l = 0, r = s.length() - 1;
    while (l < r) {
        if (s.charAt(l) != s.charAt(r)) return false;
        l++;
        r--;
    }
    return true;
}
```

### Explanation
- Two pointers compare both ends.

### Complexity
- Best: O(1) (early mismatch)
- Worst: O(n)
- Space: O(1)

### Practice Task
Reverse words in a sentence.

---

## 5) Linked Lists

### Definition
A list of nodes where each node has data and pointer to next node.

### Use
- Dynamic size
- Fast insertion/deletion when node reference is known

### When & Why Used
- When frequent insertions/deletions are needed.

### Syntax and Logic
```java
class Node {
    int data;
    Node next;
    Node(int data) { this.data = data; }
}
```

### Complexity
- Access by index: Best O(1) (head), Worst O(n)
- Insert at head: O(1)
- Insert at tail: O(n) (O(1) if tail pointer kept)
- Delete by value: O(n)

### Example
```java
public static Node reverseList(Node head) {
    Node prev = null, curr = head;
    while (curr != null) {
        Node next = curr.next;
        curr.next = prev;
        prev = curr;
        curr = next;
    }
    return prev;
}
```

### Explanation
- Reverse links one by one.

### Complexity
- Time: O(n)
- Space: O(1)

### Practice Task
Detect cycle using slow/fast pointer.

---

## 6) Stack

### Definition
LIFO (Last In, First Out).

### Use
- Undo operations
- Function call simulation
- Expression evaluation

### When & Why Used
- When recent element should be processed first.

### Syntax and Logic
```java
Stack<Integer> st = new Stack<>();
st.push(10);
st.pop();
st.peek();
```

### Complexity
- Push: O(1)
- Pop: O(1)
- Peek: O(1)

### Example
```java
public static boolean balancedParentheses(String s) {
    Stack<Character> st = new Stack<>();
    for (char c : s.toCharArray()) {
        if (c == '(') st.push(c);
        else if (c == ')') {
            if (st.isEmpty()) return false;
            st.pop();
        }
    }
    return st.isEmpty();
}
```

### Explanation
- Opening bracket pushes.
- Closing bracket pops matching opening.

### Complexity
- Time: O(n)
- Space: O(n) worst (all openings)

### Practice Task
Implement stack using array.

---

## 7) Queue

### Definition
FIFO (First In, First Out).

### Use
- Scheduling
- Buffering
- BFS in graphs

### When & Why Used
- When oldest element must be processed first.

### Syntax and Logic
```java
Queue<Integer> q = new LinkedList<>();
q.offer(1);
q.poll();
q.peek();
```

### Complexity
- Enqueue: O(1)
- Dequeue: O(1)
- Peek: O(1)

### Example
```java
public static void printOrder(Queue<String> q) {
    while (!q.isEmpty()) {
        System.out.println(q.poll());
    }
}
```

### Explanation
- Items are removed in arrival order.

### Complexity
- Time: O(n) total for n items
- Space: O(1) extra

### Practice Task
Implement queue using two stacks.

---

## 8) Hashing (HashMap / HashSet)

### Definition
Maps keys to buckets using hash function.

### Use
- Fast lookups
- Frequency counting
- Duplicate checks

### When & Why Used
- When average O(1) operations are needed.

### Syntax and Logic
```java
HashMap<String, Integer> map = new HashMap<>();
HashSet<Integer> set = new HashSet<>();
```

### Complexity (average case)
- Insert: O(1)
- Search: O(1)
- Delete: O(1)
Worst case can degrade (hash collisions) near O(n).

### Example
```java
public static char firstUniqueChar(String s) {
    Map<Character, Integer> freq = new HashMap<>();
    for (char c : s.toCharArray()) {
        freq.put(c, freq.getOrDefault(c, 0) + 1);
    }
    for (char c : s.toCharArray()) {
        if (freq.get(c) == 1) return c;
    }
    return '#';
}
```

### Explanation
- First pass: count frequency.
- Second pass: return first char with freq 1.

### Complexity
- Time: O(n)
- Space: O(k) where k = unique chars

### Practice Task
Group anagrams using HashMap.

---

## 9) Trees

### Definition
Hierarchical structure of nodes.

### Use
- Hierarchy representation
- Efficient searching/traversals

### When & Why Used
- File systems, menus, org structures.

### Syntax and Logic
```java
class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int val) { this.val = val; }
}
```

### Complexity
Depends on operation and tree shape.

### Example (Inorder)
```java
public static void inorder(TreeNode root) {
    if (root == null) return;
    inorder(root.left);
    System.out.print(root.val + " ");
    inorder(root.right);
}
```

### Explanation
- Left, root, right traversal sequence.

### Complexity
- Time: O(n)
- Space: O(h) recursion stack (h = tree height)

### Practice Task
Find number of leaf nodes.

---

## 10) Binary Search Tree (BST)

### Definition
Binary tree with rule: left < root < right.

### Use
- Ordered storage
- Faster search/insert/delete (if balanced)

### When & Why Used
- When sorted behavior needed with dynamic updates.

### Syntax and Logic
Use comparisons to move left/right.

### Complexity
- Best/Average (balanced): O(log n)
- Worst (skewed): O(n)
Reason: height becomes n in skewed tree.

### Example
```java
public static boolean searchBST(TreeNode root, int key) {
    while (root != null) {
        if (root.val == key) return true;
        if (key < root.val) root = root.left;
        else root = root.right;
    }
    return false;
}
```

### Explanation
- Each comparison eliminates one subtree.

### Practice Task
Insert and delete node in BST.

---

## 11) Heap / Priority Queue

### Definition
Complete binary tree with heap property.
- Min-heap: parent <= children
- Max-heap: parent >= children

### Use
- Top-k
- Scheduling
- Priority processing

### When & Why Used
- Need repeated min or max quickly.

### Syntax and Logic
```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
```

### Complexity
- Insert: O(log n)
- Remove top: O(log n)
- Peek top: O(1)

### Example
```java
public static int kthLargest(int[] nums, int k) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    for (int x : nums) {
        minHeap.offer(x);
        if (minHeap.size() > k) minHeap.poll();
    }
    return minHeap.peek();
}
```

### Explanation
- Maintain only k largest elements.
- Smallest among them = kth largest overall.

### Practice Task
Find k closest points to origin.

---

## 12) Trie

### Definition
Tree for storing strings character-by-character.

### Use
- Prefix search
- Autocomplete
- Dictionary checks

### When & Why Used
- Many prefix queries on words.

### Syntax and Logic
```java
class TrieNode {
    TrieNode[] child = new TrieNode[26];
    boolean isEnd;
}
```

### Complexity
If word length = L:
- Insert: O(L)
- Search: O(L)
- Prefix: O(L)
Space can be high due to many pointers.

### Example
```java
class Trie {
    TrieNode root = new TrieNode();

    void insert(String word) {
        TrieNode cur = root;
        for (char c : word.toCharArray()) {
            int idx = c - 'a';
            if (cur.child[idx] == null) cur.child[idx] = new TrieNode();
            cur = cur.child[idx];
        }
        cur.isEnd = true;
    }

    boolean search(String word) {
        TrieNode cur = root;
        for (char c : word.toCharArray()) {
            int idx = c - 'a';
            if (cur.child[idx] == null) return false;
            cur = cur.child[idx];
        }
        return cur.isEnd;
    }
}
```

### Practice Task
Implement `startsWith(prefix)`.

---

## 13) Graphs

### Definition
Set of vertices (nodes) and edges (connections).

### Use
- Social networks
- Maps/routes
- Dependencies

### When & Why Used
- Any relationship/network problem.

### Syntax and Logic (Adjacency List)
```java
List<List<Integer>> graph = new ArrayList<>();
```

### Complexity
- BFS/DFS: O(V + E)
- Space: O(V + E)

### Example (BFS)
```java
public static void bfs(List<List<Integer>> g, int src) {
    boolean[] vis = new boolean[g.size()];
    Queue<Integer> q = new LinkedList<>();
    vis[src] = true;
    q.offer(src);

    while (!q.isEmpty()) {
        int u = q.poll();
        System.out.print(u + " ");
        for (int v : g.get(u)) {
            if (!vis[v]) {
                vis[v] = true;
                q.offer(v);
            }
        }
    }
}
```

### Explanation
- Visit source.
- Expand level by level.

### Practice Task
Count connected components in undirected graph.

---

## 14) Sorting Algorithms

### Definition
Arrange elements in ascending/descending order.

### Use
- Faster searching
- Ordered reports
- Data preprocessing

### When & Why Used
- Before binary search
- When rank/order is required.

### Common Complexities
- Bubble/Selection/Insertion: O(n²)
- Merge sort: O(n log n)
- Quick sort: Avg O(n log n), Worst O(n²)
- Heap sort: O(n log n)

### Example (Merge Sort)
```java
public static void mergeSort(int[] arr, int l, int r) {
    if (l >= r) return;
    int m = l + (r - l) / 2;
    mergeSort(arr, l, m);
    mergeSort(arr, m + 1, r);
    merge(arr, l, m, r);
}
```
(Assume `merge()` combines two sorted halves.)

### Explanation
- Divide array into halves.
- Recursively sort both halves.
- Merge sorted halves.

### Complexity
- Best/Worst Time: O(n log n)
- Space: O(n)

### Practice Task
Implement quick sort with pivot explanation.

---

## 15) Searching Algorithms

### Definition
Finding target in data structure.

### Use
- Lookups, validation, retrieval.

### When & Why Used
- In almost every application.

### Types
- Linear Search
- Binary Search (sorted array)

### Complexity
- Linear: Best O(1), Worst O(n)
- Binary: Best O(1), Worst O(log n)

### Example (Binary Search)
```java
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
```

### Practice Task
Find first occurrence of target in sorted array.

---

## 16) Recursion

### Definition
Function calls itself for smaller subproblem.

### Use
- Tree traversal
- Divide and conquer
- Backtracking

### When & Why Used
- Problem naturally breaks into similar smaller parts.

### Complexity
Depends on recursion tree.
Also includes call stack space.

### Example
```java
public static int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```

### Explanation
- Base case stops recursion.
- Recursive case reduces n.

### Complexity
- Time: O(n)
- Space: O(n) call stack

### Practice Task
Compute sum of digits using recursion.

---

## 17) Dynamic Programming (DP)

### Definition
Optimization over recursion by storing subproblem results.

### Use
- Min/max/count problems with overlapping subproblems.

### When & Why Used
- Recursive solution repeats same subproblems.

### Approaches
- Memoization (top-down)
- Tabulation (bottom-up)

### Example (Fibonacci Tabulation)
```java
public static int fibDP(int n) {
    if (n <= 1) return n;
    int[] dp = new int[n + 1];
    dp[0] = 0; dp[1] = 1;
    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}
```

### Complexity
- Time: O(n)
- Space: O(n) (can optimize to O(1))

### Practice Task
Solve climbing stairs and house robber.

---

## 18) Greedy Algorithms

### Definition
Choose locally best option at each step.

### Use
- Scheduling and optimization problems.

### When & Why Used
- When local optimum leads to global optimum.

### Complexity
Problem dependent.

### Example (Activity Selection Idea)
1. Sort by finish time  
2. Pick first activity  
3. Pick next non-overlapping activity  

### Practice Task
Given intervals, find maximum non-overlapping intervals.

---

## 19) Backtracking

### Definition
Try choices, recurse, undo choice if invalid.

### Use
- N-Queens, Sudoku, permutations, subsets.

### When & Why Used
- Need all valid combinations/permutations.

### Example (Subsets)
```java
public static void subsets(int[] nums, int idx, List<Integer> cur, List<List<Integer>> ans) {
    if (idx == nums.length) {
        ans.add(new ArrayList<>(cur));
        return;
    }
    cur.add(nums[idx]);
    subsets(nums, idx + 1, cur, ans);
    cur.remove(cur.size() - 1);
    subsets(nums, idx + 1, cur, ans);
}
```

### Complexity
- Time: often exponential (e.g., O(2^n))
- Space: recursion depth O(n)

### Practice Task
Generate all permutations of a string.

---

## 20) Sliding Window and Two Pointers

### Definition
Techniques for efficient array/string traversal.

### Use
- Subarray/substring optimization
- Pair problems in sorted arrays

### When & Why Used
- Repeated range calculations
- Need O(n) optimization over O(n²)

### Example (Fixed-size window max sum)
```java
public static int maxSumK(int[] arr, int k) {
    int sum = 0;
    for (int i = 0; i < k; i++) sum += arr[i];
    int max = sum;
    for (int i = k; i < arr.length; i++) {
        sum += arr[i] - arr[i - k];
        max = Math.max(max, sum);
    }
    return max;
}
```

### Complexity
- Time: O(n)
- Space: O(1)

### Practice Task
Longest substring without repeating characters.

---

## 21) Detailed Differences Between Data Structures

## Array vs Linked List
- Array:
  - Contiguous memory
  - O(1) index access
  - Insert/delete in middle costly O(n)
- Linked List:
  - Non-contiguous nodes
  - O(n) access
  - Insert/delete easier with node reference

## Stack vs Queue
- Stack: LIFO  
- Queue: FIFO  
- Use stack for undo/backtracking; queue for scheduling/BFS.

## HashMap vs TreeMap
- HashMap:
  - Average O(1)
  - Unordered keys
- TreeMap:
  - O(log n)
  - Keys sorted

## BST vs Heap
- BST:
  - Ordered search
  - Good for range queries
- Heap:
  - Best for min/max extraction
  - Not for full ordered search

## Trie vs HashMap (for words)
- Trie: O(L) prefix/word operations, prefix-friendly
- HashMap: exact key lookup; no native prefix structure

## Tree vs Graph
- Tree: connected + acyclic + single root (usually)
- Graph: may have cycles, may be disconnected, general relations

## Practice Task
Create your own table for Search/Insert/Delete/Space/Best use-case for all structures.

---

## 22) Interview Questions with Answers (Google / Amazon / Product Companies)

1. **What is the difference between Array and Linked List?**  
   Array gives O(1) indexing but costly mid insertion/deletion. Linked list gives O(n) indexing but easier insert/delete with node references.

2. **Why is binary search O(log n)?**  
   Each step halves search space.

3. **Can binary search work on unsorted data?**  
   No, sorted order is required.

4. **Explain HashMap collision.**  
   Multiple keys map to same bucket index; handled using chaining/tree bins.

5. **BFS vs DFS use cases?**  
   BFS for shortest path in unweighted graph; DFS for deep traversal and cycle detection patterns.

6. **Why use DP instead of recursion?**  
   DP avoids repeated calculations of overlapping subproblems.

7. **What is memoization?**  
   Caching recursive results (top-down DP).

8. **Quick sort worst case and why?**  
   O(n²), when pivot divides poorly (highly unbalanced partitions).

9. **What is stable sorting?**  
   Equal elements preserve relative order (e.g., Merge sort stable, quick sort generally unstable).

10. **What is a balanced tree?**  
    Tree height near log n; gives faster operations.

11. **How to detect cycle in linked list?**  
    Floyd’s slow/fast pointer algorithm.

12. **What is topological sort?**  
    Ordering of DAG where edge u→v means u appears before v.

13. **Difference between process and thread?**  
    Process has separate memory; threads share process memory.

14. **When to use heap?**  
    Top-k, priority scheduling, streaming min/max.

15. **What is amortized analysis?**  
    Average cost over sequence of operations (e.g., dynamic array resize behavior).

16. **Why StringBuilder over String concatenation in loop?**  
    String is immutable; repeated concatenation creates many objects.

17. **What is space-time tradeoff?**  
    Use more memory to reduce runtime (e.g., hash map caching).

18. **How do you optimize brute force solutions in interviews?**  
    Identify repeated work, use hashing/two pointers/sliding window/DP.

19. **What if interviewer asks for best and worst case?**  
    Explain both with input scenarios and why runtime changes.

20. **Interview solving strategy in product companies?**  
    Clarify problem, state brute force, optimize, analyze complexity, test edge cases, communicate clearly.

---

## 23) Beginner Practice Roadmap (6 Weeks)

### Week 1
Complexity + Arrays + Strings

### Week 2
Linked List + Stack + Queue

### Week 3
Hashing + Trees + BST

### Week 4
Heap + Graph basics + Searching + Sorting

### Week 5
Recursion + Backtracking + DP basics

### Week 6
Mixed interview questions + timed mock practice

### Daily Template
- 30 mins concept revision
- 60 mins coding (2 easy + 1 medium)
- 15 mins complexity analysis writing
- 15 mins mistake review

---

## Final Note
Consistency beats intensity.  
If you practice daily and revise patterns weekly, DSA will become natural and interview confidence will grow quickly.
