# Beginner Data Structures & Algorithms Handbook (Version 2)

A highly detailed beginner-friendly guide to complete Data Structures and Algorithms using Java.

This handbook covers each concept in the format:
1. Definition
2. Use of the concept
3. When & why it is used
4. Syntax and logic
5. Basic Java code with detailed explanation
6. Small hands-on practice task

It also includes:
- Detailed differences between major data structures
- Interview questions and answers asked in product companies (Google, Amazon, etc.)

---

## Table of Contents
1. Introduction to DSA
2. Time and Space Complexity
3. Arrays
4. Strings
5. Linked Lists
6. Stacks
7. Queues
8. Hashing (HashMap/HashSet)
9. Trees
10. Binary Search Trees
11. Heaps and Priority Queues
12. Trie
13. Graphs
14. Sorting Algorithms
15. Searching Algorithms
16. Recursion
17. Dynamic Programming (Beginner)
18. Greedy Algorithms
19. Backtracking
20. Sliding Window and Two Pointers
21. Detailed Differences Between Data Structures
22. Interview Questions with Answers

---

## 1) Introduction to DSA

### Definition
Data Structures are ways to organize and store data. Algorithms are step-by-step procedures to solve problems.

### Use
- To store data efficiently
- To perform operations quickly
- To solve coding problems logically

### When & Why Used
Used in almost every software system, from search engines to mobile apps. Choosing the right structure improves performance.

### Syntax and Logic
No direct syntax; this is foundational knowledge.

### Java Example
```java
int[] marks = {85, 90, 78}; // data structure (array)

// algorithm: find max
int max = marks[0];
for (int i = 1; i < marks.length; i++) {
    if (marks[i] > max) max = marks[i];
}
System.out.println(max);
```

### Code Explanation
- Array stores values.
- Loop compares all values to find largest.

### Practice Task
Write Java code to find minimum value in an array.

---

## 2) Time and Space Complexity

### Definition
Complexity measures how efficient code is in terms of time and memory.

### Use
To compare different solutions and choose optimal one.

### When & Why Used
Used while designing algorithms and during interviews.

### Syntax and Logic
Big-O notation:
- O(1), O(log n), O(n), O(n log n), O(n^2)

### Java Example
```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) return i;
    }
    return -1;
}
```

### Code Explanation
- Checks each element once.
- Worst case: all elements checked → O(n)
- Extra space: O(1)

### Practice Task
Analyze complexity of binary search.

---

## 3) Arrays

### Definition
An array stores same-type elements in contiguous memory.

### Use
Fast indexing and iteration.

### When & Why Used
Used when size is known or near-known and random access is needed.

### Syntax and Logic
```java
int[] arr = new int[5];
int[] nums = {1, 2, 3};
```

### Java Example
```java
public static int sum(int[] arr) {
    int total = 0;
    for (int x : arr) total += x;
    return total;
}
```

### Code Explanation
- `total` starts at 0.
- Each element added once.
- Returns total sum.

### Practice Task
Find second largest element without sorting.

---

## 4) Strings

### Definition
A String is a sequence of characters.

### Use
Text processing: validation, parsing, searching.

### When & Why Used
Used whenever text data is involved.

### Syntax and Logic
```java
String s = "hello";
StringBuilder sb = new StringBuilder("hello");
```

### Java Example
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

### Code Explanation
- Compare first and last, then move inward.
- If any mismatch, not palindrome.

### Practice Task
Count vowels and consonants in a string.

---

## 5) Linked Lists

### Definition
A linked list is a chain of nodes where each node points to next.

### Use
Efficient insert/delete when position pointer is known.

### When & Why Used
Used when dynamic size and frequent modifications are needed.

### Syntax and Logic
```java
class Node {
    int data;
    Node next;
    Node(int data) { this.data = data; }
}
```

### Java Example
```java
public static Node insertAtHead(Node head, int val) {
    Node newNode = new Node(val);
    newNode.next = head;
    return newNode;
}
```

### Code Explanation
- New node created.
- Points to current head.
- New node becomes new head.

### Practice Task
Reverse a singly linked list iteratively.

---

## 6) Stacks

### Definition
Stack is LIFO structure.

### Use
Undo operations, recursion simulation, expression parsing.

### When & Why Used
Used when most recent element should be processed first.

### Syntax and Logic
```java
Stack<Integer> st = new Stack<>();
st.push(10);
st.pop();
```

### Java Example
```java
public static String reverseWord(String s) {
    Stack<Character> st = new Stack<>();
    for (char c : s.toCharArray()) st.push(c);
    StringBuilder sb = new StringBuilder();
    while (!st.isEmpty()) sb.append(st.pop());
    return sb.toString();
}
```

### Code Explanation
- Push all chars.
- Pop gives reverse order.

### Practice Task
Implement Min Stack (push, pop, getMin).

---

## 7) Queues

### Definition
Queue is FIFO structure.

### Use
Task scheduling, buffering, BFS.

### When & Why Used
Used when first inserted item must be processed first.

### Syntax and Logic
```java
Queue<Integer> q = new LinkedList<>();
q.offer(1);
q.poll();
```

### Java Example
```java
public static void printQueue(Queue<Integer> q) {
    while (!q.isEmpty()) {
        System.out.print(q.poll() + " ");
    }
}
```

### Code Explanation
- Removes and prints elements in insertion order.

### Practice Task
Implement circular queue using array.

---

## 8) Hashing (HashMap/HashSet)

### Definition
Hashing maps keys to indices for fast operations.

### Use
Fast lookup, frequency count, duplicates detection.

### When & Why Used
Used when quick average O(1) search/insert is needed.

### Syntax and Logic
```java
HashMap<String, Integer> map = new HashMap<>();
HashSet<Integer> set = new HashSet<>();
```

### Java Example
```java
public static boolean hasDuplicate(int[] arr) {
    HashSet<Integer> set = new HashSet<>();
    for (int x : arr) {
        if (set.contains(x)) return true;
        set.add(x);
    }
    return false;
}
```

### Code Explanation
- Store each value in set.
- If already exists, duplicate found.

### Practice Task
Find first unique character in string.

---

## 9) Trees

### Definition
A hierarchical structure with nodes and edges.

### Use
Represent hierarchical data (filesystem, organization).

### When & Why Used
Used for fast search/traversal and hierarchy modeling.

### Syntax and Logic
```java
class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int v) { val = v; }
}
```

### Java Example
```java
public static int countNodes(TreeNode root) {
    if (root == null) return 0;
    return 1 + countNodes(root.left) + countNodes(root.right);
}
```

### Code Explanation
- Base case null gives 0.
- Count current + left + right.

### Practice Task
Find height of binary tree.

---

## 10) Binary Search Tree (BST)

### Definition
A tree where left < root < right.

### Use
Ordered data storage with efficient operations.

### When & Why Used
Used for searchable ordered collections.

### Syntax and Logic
Use recursive or iterative insert/search/delete.

### Java Example
```java
public static TreeNode insertBST(TreeNode root, int key) {
    if (root == null) return new TreeNode(key);
    if (key < root.val) root.left = insertBST(root.left, key);
    else if (key > root.val) root.right = insertBST(root.right, key);
    return root;
}
```

### Code Explanation
- Find correct position based on BST rule.
- Insert where null is found.

### Practice Task
Implement search and inorder traversal of BST.

---

## 11) Heap and Priority Queue

### Definition
Heap is complete tree with min/max property.

### Use
Efficient min/max extraction.

### When & Why Used
Used for top-k, scheduling, shortest path algorithms.

### Syntax and Logic
```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
```

### Java Example
```java
public static int kthSmallest(int[] arr, int k) {
    PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
    for (int x : arr) {
        maxHeap.offer(x);
        if (maxHeap.size() > k) maxHeap.poll();
    }
    return maxHeap.peek();
}
```

### Code Explanation
- Keep only k smallest elements in maxHeap.
- Top is kth smallest.

### Practice Task
Find kth largest element using min heap.

---

## 12) Trie

### Definition
Trie is tree-like structure for strings by characters.

### Use
Prefix search and autocomplete.

### When & Why Used
Used when prefix operations are frequent.

### Syntax and Logic
Character-by-character traversal.

### Java Example
```java
class TrieNode {
    TrieNode[] child = new TrieNode[26];
    boolean isEnd;
}

class Trie {
    TrieNode root = new TrieNode();

    void insert(String word) {
        TrieNode cur = root;
        for (char c : word.toCharArray()) {
            int i = c - 'a';
            if (cur.child[i] == null) cur.child[i] = new TrieNode();
            cur = cur.child[i];
        }
        cur.isEnd = true;
    }
}
```

### Code Explanation
- Follow/create path for each character.
- Mark last node as word end.

### Practice Task
Implement `search` and `startsWith`.

---

## 13) Graphs

### Definition
Graph is a set of vertices and edges.

### Use
Networks, maps, dependencies, recommendations.

### When & Why Used
Used for relation-based problems.

### Syntax and Logic
Adjacency list representation preferred for sparse graphs.

### Java Example (DFS)
```java
public static void dfs(int u, List<List<Integer>> g, boolean[] vis) {
    vis[u] = true;
    System.out.print(u + " ");
    for (int v : g.get(u)) {
        if (!vis[v]) dfs(v, g, vis);
    }
}
```

### Code Explanation
- Visit current node.
- Recursively visit unvisited neighbors.

### Practice Task
Implement BFS and detect connected components.

---

## 14) Sorting Algorithms

### Definition
Sorting arranges data in order.

### Use
Faster searching and better organization.

### When & Why Used
Used before binary search, reports, ranking.

### Syntax and Logic
Common beginner sorts: Bubble, Selection, Insertion.

### Java Example (Insertion Sort)
```java
public static void insertionSort(int[] arr) {
    for (int i = 1; i < arr.length; i++) {
        int key = arr[i], j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```

### Code Explanation
- Keep left part sorted.
- Insert current element in correct position.

### Practice Task
Implement merge sort.

---

## 15) Searching Algorithms

### Definition
Searching finds target element in data.

### Use
Retrieving required records quickly.

### When & Why Used
In databases, filtering, validation.

### Syntax and Logic
- Linear search for unsorted data
- Binary search for sorted data

### Java Example (Binary Search)
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
Find first and last index of target in sorted array.

---

## 16) Recursion

### Definition
A function solving problem by calling itself.

### Use
Tree traversal, divide-and-conquer, backtracking.

### When & Why Used
Used when problem can be broken into similar smaller subproblems.

### Java Example
```java
public static int sumN(int n) {
    if (n == 0) return 0;
    return n + sumN(n - 1);
}
```

### Code Explanation
- Base case at n=0.
- Sum current n with result of n-1.

### Practice Task
Print numbers from 1 to n recursively.

---

## 17) Dynamic Programming (Beginner)

### Definition
An optimization of recursion by storing repeated sub-results.

### Use
Complex optimization/counting problems.

### When & Why Used
When recursion has overlapping subproblems.

### Java Example (Climbing Stairs)
```java
public static int climbStairs(int n) {
    if (n <= 2) return n;
    int[] dp = new int[n + 1];
    dp[1] = 1; dp[2] = 2;
    for (int i = 3; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}
```

### Practice Task
Solve house robber basic problem.

---

## 18) Greedy Algorithms

### Definition
Greedy picks best immediate option at each step.

### Use
Scheduling and optimization with local decisions.

### When & Why Used
When local best choice leads to global best answer.

### Java Example (Activity Count idea)
```java
// After sorting by end time, count non-overlapping intervals.
```

### Practice Task
Given intervals, remove minimum overlaps.

---

## 19) Backtracking

### Definition
Try all possibilities, undo choice when needed.

### Use
Combinations, permutations, puzzle solving.

### When & Why Used
When exhaustive search with pruning is needed.

### Java Example (Subsets)
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

### Practice Task
Generate all permutations of array.

---

## 20) Sliding Window and Two Pointers

### Definition
Techniques to optimize array/string traversal.

### Use
Subarray and substring problems.

### When & Why Used
Used when contiguous range or pair relation is required.

### Java Example (Max sum of size k)
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

### Practice Task
Find longest substring without repeating characters.

---

## 21) Detailed Differences Between Data Structures

### Array vs Linked List
- Array: contiguous memory, O(1) indexing, costly middle insert/delete.
- Linked List: non-contiguous, O(n) access, easy insert/delete with node reference.

### Stack vs Queue
- Stack: LIFO
- Queue: FIFO

### HashMap vs TreeMap
- HashMap: average O(1), unordered.
- TreeMap: O(log n), sorted keys.

### BST vs Heap
- BST: supports ordered search/range.
- Heap: optimized for min/max retrieval only.

### Trie vs HashMap
- Trie: prefix-based operations.
- HashMap: exact key lookup.

### Tree vs Graph
- Tree: connected acyclic graph with one root.
- Graph: generic relation model, can have cycles/disconnected parts.

### Segment Tree vs Fenwick Tree (intro)
- Fenwick: simpler for prefix sums.
- Segment Tree: more flexible range queries and updates.

**Practice Task:**
Create a complexity comparison table for all above.

---

## 22) Interview Questions with Answers

### 1. What is the difference between array and linked list?
Array has O(1) index access but costly middle insertions. Linked list has O(n) access but easy insertion/deletion at node.

### 2. Why binary search needs sorted array?
Because it relies on order to eliminate half search space.

### 3. Explain HashMap collision.
Different keys may map to same bucket; handled using chaining/tree bins.

### 4. BFS vs DFS?
BFS explores level-wise using queue; DFS explores depth-first using stack/recursion.

### 5. What is recursion base case?
Condition that stops further recursive calls.

### 6. Why use dynamic programming?
To avoid recalculating overlapping subproblems.

### 7. Quick sort worst-case complexity?
O(n^2) when partitions are highly unbalanced.

### 8. What is heap used for?
Priority handling, top-k elements, scheduling.

### 9. What is balanced BST benefit?
Keeps height around log n, making operations fast.

### 10. What is topological sort?
Linear ordering of DAG where prerequisite comes first.

### 11. Difference between process and thread?
Process has separate memory space; threads share memory within process.

### 12. What is two-pointer technique?
Use two indices to solve pair/subarray problems efficiently.

### 13. What is sliding window?
Maintain moving range to optimize contiguous segment problems.

### 14. How to detect cycle in linked list?
Use slow-fast pointers (Floyd’s algorithm).

### 15. How to prepare for product-company interviews?
Master core DSA patterns, practice timed problems, explain logic clearly, and analyze complexity.

---

## Suggested Beginner Practice Plan (6 Weeks)
- Week 1: Complexity, Arrays, Strings
- Week 2: Linked List, Stack, Queue
- Week 3: Hashing, Trees, BST
- Week 4: Heap, Graph basics, Sorting, Searching
- Week 5: Recursion, Backtracking, DP intro
- Week 6: Mixed interview sets + revision

Daily:
- 1 concept revision
- 3 coding questions (2 easy + 1 medium)
- Complexity write-up for each solution

---

Keep this handbook for revision and build strong fundamentals before moving to advanced topics.
