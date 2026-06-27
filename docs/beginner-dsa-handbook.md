# Beginner Data Structures & Algorithms Handbook (Java)

A complete beginner-friendly guide to Data Structures and Algorithms (DSA) with Java syntax, simple logic explanations, example code, how the code works, concept differences, practice tasks, and interview Q&A.

---

## Table of Contents
1. Introduction to DSA
2. Time and Space Complexity
3. Arrays
4. Strings
5. Linked Lists
6. Stack
7. Queue
8. Hashing (HashMap/HashSet)
9. Trees
10. Binary Search Tree (BST)
11. Heap and Priority Queue
12. Trie
13. Graphs
14. Sorting Algorithms
15. Searching Algorithms
16. Recursion
17. Dynamic Programming (Beginner Intro)
18. Greedy Algorithms
19. Backtracking
20. Differences Between Data Structures (Detailed)
21. Interview Questions with Answers

---

## 1) Introduction to DSA

### What is Data Structure?
A Data Structure is a way to store and organize data so it can be used efficiently.

Examples:
- Array
- Linked List
- Stack
- Queue
- Tree
- Graph

### What is an Algorithm?
An Algorithm is a step-by-step method to solve a problem.

Example:
- To find a number in a sorted array, we use Binary Search.

### Why learn DSA?
- Write efficient code
- Solve coding interview problems
- Build strong problem-solving skills

**Practice task:**
Write one real-life example each for data structure and algorithm.

---

## 2) Time and Space Complexity

### Time Complexity
How long an algorithm takes based on input size `n`.

Common complexities:
- `O(1)` constant
- `O(log n)` logarithmic
- `O(n)` linear
- `O(n log n)`
- `O(n^2)` quadratic

### Space Complexity
How much extra memory an algorithm uses.

### Java Example
```java
public static int findMax(int[] arr) {
    int max = arr[0];
    for (int i = 1; i < arr.length; i++) {
        if (arr[i] > max) max = arr[i];
    }
    return max;
}
```

### How this works
- It scans each element once.
- Time: `O(n)`
- Extra Space: `O(1)`

**Practice task:**
Find complexity of linear search, binary search, and bubble sort.

---

## 3) Arrays

Array stores elements in continuous memory.

### Operations
- Access by index: `O(1)`
- Search: `O(n)`
- Insert/Delete at end: `O(1)` (average)
- Insert/Delete middle: `O(n)`

### Java Syntax
```java
int[] arr = {10, 20, 30, 40};
System.out.println(arr[2]); // 30
```

### Example: Sum of Array
```java
public static int sumArray(int[] arr) {
    int sum = 0;
    for (int num : arr) sum += num;
    return sum;
}
```

### How this works
- Loop through each element.
- Add to `sum`.

**Practice task:**
Find second largest element in an array.

---

## 4) Strings

In Java, `String` is immutable (cannot change directly).
Use `StringBuilder` for frequent modifications.

### Java Syntax
```java
String s = "hello";
StringBuilder sb = new StringBuilder(s);
sb.append(" world");
```

### Example: Reverse String
```java
public static String reverse(String s) {
    char[] ch = s.toCharArray();
    int l = 0, r = ch.length - 1;
    while (l < r) {
        char t = ch[l];
        ch[l] = ch[r];
        ch[r] = t;
        l++; r--;
    }
    return new String(ch);
}
```

### How this works
- Converts string to char array.
- Swaps characters from both ends.

**Practice task:**
Check if a string is palindrome.

---

## 5) Linked Lists

Linked List is a sequence of nodes where each node stores:
- data
- pointer to next node

### Types
- Singly Linked List
- Doubly Linked List
- Circular Linked List

### Java Node
```java
class Node {
    int data;
    Node next;
    Node(int data) { this.data = data; }
}
```

### Example: Traverse List
```java
public static void printList(Node head) {
    Node curr = head;
    while (curr != null) {
        System.out.print(curr.data + " ");
        curr = curr.next;
    }
}
```

### How this works
- Start at head.
- Move node by node until `null`.

**Practice task:**
Insert a node at the beginning and at the end.

---

## 6) Stack

Stack follows **LIFO** (Last In, First Out).

### Common operations
- push
- pop
- peek

### Java Syntax
```java
Stack<Integer> st = new Stack<>();
st.push(10);
st.push(20);
int top = st.pop(); // 20
```

### Example: Balanced Parentheses
```java
import java.util.*;

public static boolean isBalanced(String s) {
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

### How this works
- Push opening bracket.
- On closing bracket, pop one.
- End stack should be empty.

**Practice task:**
Implement stack using array.

---

## 7) Queue

Queue follows **FIFO** (First In, First Out).

### Operations
- offer (enqueue)
- poll (dequeue)
- peek

### Java Syntax
```java
Queue<Integer> q = new LinkedList<>();
q.offer(10);
q.offer(20);
int x = q.poll(); // 10
```

### Example: Simple Queue Processing
```java
public static void processQueue() {
    Queue<String> q = new LinkedList<>();
    q.offer("A");
    q.offer("B");
    while (!q.isEmpty()) {
        System.out.println(q.poll());
    }
}
```

### How this works
- Items are removed in insertion order.

**Practice task:**
Implement queue using two stacks.

---

## 8) Hashing (HashMap / HashSet)

Hashing stores key-value pairs for fast access.

### Java Syntax
```java
HashMap<String, Integer> map = new HashMap<>();
map.put("apple", 3);
int val = map.get("apple");
```

### Example: Frequency Count
```java
public static Map<Character, Integer> freq(String s) {
    Map<Character, Integer> map = new HashMap<>();
    for (char c : s.toCharArray()) {
        map.put(c, map.getOrDefault(c, 0) + 1);
    }
    return map;
}
```

### How this works
- For each char, increment its count in map.

**Practice task:**
Find first non-repeating character in a string.

---

## 9) Trees

A tree is a hierarchical data structure.

### Terms
- Root
- Parent / Child
- Leaf
- Height

### Binary Tree
Each node has at most 2 children.

### Java Node
```java
class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int val) { this.val = val; }
}
```

### Example: Inorder Traversal
```java
public static void inorder(TreeNode root) {
    if (root == null) return;
    inorder(root.left);
    System.out.print(root.val + " ");
    inorder(root.right);
}
```

### How this works
- Left subtree first
- Then root
- Then right subtree

**Practice task:**
Write preorder and postorder traversal.

---

## 10) Binary Search Tree (BST)

BST rule:
- Left subtree values < root
- Right subtree values > root

### Example: Search in BST
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

### How this works
- Uses BST property to skip half path.

**Practice task:**
Implement insert in BST.

---

## 11) Heap and Priority Queue

Heap is a complete binary tree.

- Min Heap: smallest at top
- Max Heap: largest at top

### Java (Min Heap)
```java
PriorityQueue<Integer> pq = new PriorityQueue<>();
pq.offer(5);
pq.offer(1);
pq.offer(3);
System.out.println(pq.poll()); // 1
```

### Practice use case
Find kth largest/smallest element.

**Practice task:**
Find 3rd largest element in an array using heap.

---

## 12) Trie

Trie is used for string prefix operations.

### Use cases
- Autocomplete
- Dictionary
- Prefix matching

### Simple structure
```java
class TrieNode {
    TrieNode[] child = new TrieNode[26];
    boolean isEnd;
}
```

**Practice task:**
Implement `insert` and `search` in Trie.

---

## 13) Graphs

Graph = vertices (nodes) + edges.

### Types
- Directed / Undirected
- Weighted / Unweighted

### Representation (Adjacency List)
```java
List<List<Integer>> graph = new ArrayList<>();
```

### BFS Example
```java
public static void bfs(List<List<Integer>> g, int src) {
    boolean[] vis = new boolean[g.size()];
    Queue<Integer> q = new LinkedList<>();
    q.offer(src);
    vis[src] = true;

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

### How this works
- Visits level by level from source.

**Practice task:**
Write DFS traversal for graph.

---

## 14) Sorting Algorithms

### Bubble Sort
Repeatedly swap adjacent wrong-order elements.

```java
public static void bubbleSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int t = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = t;
            }
        }
    }
}
```

Time: `O(n^2)`

### Better sorts to learn
- Merge Sort: `O(n log n)`
- Quick Sort: average `O(n log n)`

**Practice task:**
Implement merge sort.

---

## 15) Searching Algorithms

### Linear Search
Check each element one by one.
Time: `O(n)`

### Binary Search (sorted array)
Time: `O(log n)`

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

**Practice task:**
Count occurrences of a target in sorted array.

---

## 16) Recursion

Function calls itself to solve smaller problem.

### Example: Factorial
```java
public static int fact(int n) {
    if (n == 0 || n == 1) return 1;
    return n * fact(n - 1);
}
```

### How this works
- Base case stops recursion.
- Recursive case reduces problem size.

**Practice task:**
Print Fibonacci sequence using recursion.

---

## 17) Dynamic Programming (Beginner Intro)

DP is used when:
- Overlapping subproblems
- Optimal substructure

### Example: Fibonacci with DP
```java
public static int fibDP(int n) {
    if (n <= 1) return n;
    int[] dp = new int[n + 1];
    dp[0] = 0;
    dp[1] = 1;
    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}
```

### How this works
- Stores previously computed results.
- Avoids repeated recursion calls.

**Practice task:**
Solve climbing stairs problem using DP.

---

## 18) Greedy Algorithms

Greedy chooses best option at current step.

Example problem: Coin change (for valid systems), activity selection.

**Practice task:**
Given intervals, find max non-overlapping intervals.

---

## 19) Backtracking

Try a choice, go deeper, and undo if not valid.

Examples:
- N-Queens
- Sudoku
- Subsets/Permutations

### Example: Generate Subsets
```java
public static void subsets(int[] nums, int idx, List<Integer> cur, List<List<Integer>> ans) {
    if (idx == nums.length) {
        ans.add(new ArrayList<>(cur));
        return;
    }
    // include
    cur.add(nums[idx]);
    subsets(nums, idx + 1, cur, ans);
    cur.remove(cur.size() - 1);
    // exclude
    subsets(nums, idx + 1, cur, ans);
}
```

**Practice task:**
Generate all permutations of a string.

---

## 20) Differences Between Data Structures (Detailed)

### Array vs Linked List
- Array: fast index access `O(1)`, fixed/resize cost
- Linked List: dynamic size, slower access `O(n)`, easy insertion/deletion at known node

### Stack vs Queue
- Stack: LIFO
- Queue: FIFO

### HashMap vs TreeMap
- HashMap: average `O(1)`, no sorted order
- TreeMap: `O(log n)`, sorted keys

### BST vs Heap
- BST: ordered search and range queries
- Heap: quick min/max retrieval

### Graph vs Tree
- Tree: no cycle, connected, N nodes with N-1 edges
- Graph: can have cycles, can be disconnected

### Trie vs HashMap (for words)
- Trie: best for prefix search
- HashMap: best for exact lookup

**Practice task:**
Create your own comparison table with operations: search, insert, delete, memory, use case.

---

## 21) Interview Questions with Answers (Google/Amazon/Product Companies)

### Q1. What is the difference between Array and Linked List?
**Answer:** Arrays support O(1) indexing but costly middle insert/delete. Linked list has O(n) access but flexible insert/delete with references.

### Q2. Why is binary search faster than linear search?
**Answer:** Binary search halves search space each step (`O(log n)`) but needs sorted data.

### Q3. When should we use HashMap?
**Answer:** For fast key-based lookup, counting, caching, and mapping relations.

### Q4. Explain stack overflow in recursion.
**Answer:** Too many recursive calls without proper base case fill call stack and crash.

### Q5. What is difference between BFS and DFS?
**Answer:** BFS explores level-wise (queue), DFS depth-wise (stack/recursion).

### Q6. Why do we need Dynamic Programming?
**Answer:** To avoid recomputing same subproblems and optimize recursion.

### Q7. What is a balanced tree?
**Answer:** A tree where height remains near `log n`, giving efficient operations.

### Q8. Why can quicksort be slow in worst case?
**Answer:** Bad pivot can create unbalanced partitions leading to `O(n^2)`.

### Q9. What is collision in HashMap?
**Answer:** Two keys map to same bucket index. Resolved by chaining/tree bins.

### Q10. Explain heap use in real problems.
**Answer:** Scheduling tasks, kth largest/smallest, streaming median, priority processing.

### Q11. What are stable and unstable sorting algorithms?
**Answer:** Stable sort keeps relative order of equal elements (e.g., Merge Sort), unstable may change it (e.g., Quick Sort usually).

### Q12. What is topological sort?
**Answer:** Linear ordering of DAG nodes where edge `u -> v` means `u` appears before `v`.

### Q13. What is memoization?
**Answer:** Caching recursive results to avoid repeated work.

### Q14. What is difference between process and thread?
**Answer:** Process has separate memory; threads share process memory.

### Q15. Interview strategy tip?
**Answer:** Clarify constraints, start brute force, optimize step-by-step, explain complexity, test edge cases.

---

## Final Practice Plan (Beginner)

- Week 1: Arrays + Strings + Complexity
- Week 2: Linked List + Stack + Queue
- Week 3: Hashing + Trees + BST
- Week 4: Heap + Graph Basics + Sorting + Searching
- Week 5: Recursion + Backtracking + DP intro
- Week 6: Mixed interview practice

Daily target:
- 1 concept revision
- 2 easy + 1 medium coding problem
- Write complexity for each solution

---

Keep practicing consistently. DSA becomes easy when you revise patterns and solve problems regularly.
