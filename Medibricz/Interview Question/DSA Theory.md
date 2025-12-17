# 🔹 **Array & String Concepts (1–10)**

---

## **1. Difference between array and linked list**

### **Array**

- Contiguous memory allocation
    
- Fixed size
    
- O(1) random access
    
- Insert/delete in the middle is costly (O(n))
    

### **Linked List**

- Non-contiguous memory allocation
    
- Dynamic size
    
- No random access (O(n) traversal)
    
- Insert/delete is O(1) when you have the pointer
    

**Key idea:**  
Arrays → Fast access, slow insertion  
Linked Lists → Slow access, fast insertion

---

## **2. Why is accessing an element in an array O(1)?**

Because arrays store data **contiguously**, so the address of any element is computed as:

```
address = base + index * size_of_element
```

No traversal or scanning is needed → **constant time lookup**.

---

## **3. Difference between stack memory and heap memory**

### **Stack Memory**

- Stores function frames, local variables
    
- Automatically managed
    
- Fast allocation/deallocation
    
- Size is limited
    
- LIFO structure
    

### **Heap Memory**

- Stores dynamic objects
    
- Managed manually (or via GC)
    
- Slower allocation
    
- Much larger memory
    
- No strict ordering
    

---

## **4. Explain sliding window technique**

A **sliding window** is a technique to efficiently solve problems involving **subarrays or substrings** in linear time.

### How it works:

- Maintain a window (left, right pointers)
    
- Expand right pointer to include new data
    
- Shrink left pointer when constraints break
    
- Keep track of best or required result
    

### Used in:

- Longest substring without repeating characters
    
- Maximum sum subarray of size K
    
- Anagram checks
    

It reduces O(n²) problems to **O(n)**.

---

## **5. Difference between shallow copy and deep copy**

### **Shallow Copy**

- Copies the **references**, not underlying objects
    
- Changes in nested objects reflect in both
    

### **Deep Copy**

- Recursively copies all nested objects
    
- Independent copies → changes do NOT reflect
    

---

## **6. Why is reversing a string O(n)?**

Because each character must be visited **once** to swap positions.  
Even if done in-place, you still need to touch all characters → O(n).

---

## **7. What is the two-pointer technique?**

Using two indexes/pointers to iterate over data efficiently.

### Example use cases:

- Sorted two-sum
    
- Merging two sorted arrays
    
- Removing duplicates
    
- Reversing a string
    
- Palindrome check
    

This reduces nested loops → O(n) instead of O(n²).

---

## **8. How does binary search work and why is it O(log n)?**

### Working:

- Compare target with middle element
    
- Eliminate half of array each step
    
- Repeat on remaining half
    

### Why O(log n)?

Each step cuts the search space in half → logarithmic time growth.

---

## **9. Difference between subarray, substring & subsequence**

|Concept|Definition|Must be contiguous?|
|---|---|---|
|Subarray|Part of an array|✔ Yes|
|Substring|Part of a string|✔ Yes|
|Subsequence|Can skip elements|✖ No|

Example for "abc":  
Subsequences include "ac", "b", "abc" but substrings do NOT.

---

## **10. What is prefix sum? Why useful?**

Prefix sum array stores cumulative sum:

```
prefix[i] = sum(arr[0 … i])
```

### Why useful?

- Query sum of any range in O(1)
    
- Great for:
    
    - Range sum
        
    - Difference arrays
        
    - Histogram problems
        

---

# 🔹 **Time & Space Complexity (11–15)**

---

## **11. What is Big-O notation and why is it important?**

Big-O describes **how runtime or space grows** with input size.  
It helps compare algorithms independent of:

- Hardware
    
- Language
    
- System load
    

It hides constants and focuses on **growth rate**.

---

## **12. Explain time complexity of bubble sort vs merge sort**

### **Bubble Sort**

- Worst: O(n²)
    
- Average: O(n²)
    
- Best: O(n) (if optimized)
    
- Simple but slow
    
- Repeated adjacent swaps
    

### **Merge Sort**

- Worst: O(n log n)
    
- Average: O(n log n)
    
- Best: O(n log n)
    
- Fast and stable
    
- Uses divide-and-conquer
    

Merge sort beats bubble sort for all large inputs.

---

## **13. What is the space complexity of recursive functions? Why?**

Each recursive call adds a **stack frame**.  
Thus, space complexity depends on **maximum recursion depth**.

Example:

- DFS → O(h) where h = tree height
    
- Factorial(n) → O(n)
    

---

## **14. Why is hash map access O(1)?**

Hashing breaks data into buckets.

### Expected O(1) because:

- Compute hash in constant time
    
- Jump directly to index
    
- Collision lists are short on average
    

Worst-case is O(n), but good hashing keeps average O(1).

---

## **15. Worst-case time complexity of quicksort? When does it occur?**

### Worst-case: **O(n²)**

Occurs when pivot selection is poor.

Examples:

- Already sorted array
    
- Reverse sorted
    
- Pivot always smallest/largest
    

### Average: **O(n log n)**

Using random pivot avoids worst-case.

---

# 🔹 **Stack, Queue, Hashing (16–20)**

---

## **16. Problems suited for stacks**

- Balanced parentheses
    
- Undo/redo operations
    
- DFS traversal
    
- Reverse a string
    
- Evaluate expressions (postfix/prefix)
    

Stack is perfect for **LIFO** operations.

---

## **17. Difference between queue and deque**

### Queue

- FIFO
    
- Operates like people in line
    
- push → back, pop → front
    

### Deque (Double-ended queue)

- Insert/delete from both ends
    
- More flexible
    
- Used in sliding window max algorithms
    

---

## **18. What happens in case of a hash collision?**

Two keys produce same hash (rare but possible).

Collision Resolution Methods:

- **Chaining (Linked list)**
    
- **Open addressing (linear/quadratic probing)**
    
- **Double hashing**
    

Hashmaps rely on good hash functions to minimize collisions.

---

## **19. Explain LRU cache**

LRU = **Least Recently Used**.

### Rules:

- Each access makes item "recent"
    
- When capacity full → remove least recently used item
    
- Typically implemented using:
    
    - **Hashmap** (for O(1) lookup)
        
    - **Doubly-linked list** (for O(1) removal/move)
        

---

## **20. Why are hashmaps used for frequency counting?**

- O(1) average insertion & lookup
    
- Dynamic key storage
    
- Works for string characters, words, numbers, etc.
    
- Much faster than arrays when keys are large or non-numeric
    

---

# 🔹 **Trees & Graphs (21–26)**

---

## **21. Difference between a tree and a graph**

### **Tree**

- No cycles
    
- Exactly (n−1) edges
    
- Has a root
    
- Connected
    

### **Graph**

- May have cycles or disconnected components
    
- Can be directed or undirected
    

All trees are graphs, but not all graphs are trees.

---

## **22. Explain in-order, pre-order, post-order traversal**

Given a node: Left (L), Root (R), Right (R)

### **In-order (L, R, R)**

Left → Root → Right  
Used to get **sorted output** from BST.

### **Pre-order (R, L, R)**

Root → Left → Right  
Used to create copy of tree or prefix notation.

### **Post-order (L, R, R)**

Left → Right → Root  
Used for deletion, freeing memory, postfix notation.

---

## **23. What is the height of a binary tree?**

Height = number of edges in the **longest path** from root to leaf.

For empty tree: height = -1  
For single-node tree: height = 0

---

## **24. Difference between BFS and DFS**

### **BFS**

- Uses queue
    
- Level-by-level traversal
    
- Finds shortest path in unweighted graph
    

### **DFS**

- Uses stack / recursion
    
- Goes deep before backtracking
    
- Good for detecting cycles, topological sort
    

---

## **25. What is a balanced BST?**

A tree where the height is kept **minimal** by rebalancing operations.

Examples:

- **AVL Tree**
    
- **Red-Black Tree**
    
- **B-tree**
    

Balanced trees guarantee **O(log n)** operations.

---

## **26. What is a cycle in a graph? How to detect?**

A path where you start and end on the **same node** without repeating edges.

### Detection:

- **DFS with visited + recursion stack** (directed)
    
- **Union-Find / DSU** (undirected)
    

---

# 🔹 **Algorithms & Logic (27–30)**

---

## **27. What is dynamic programming? Give a real example.**

DP is an optimization technique for problems with **overlapping subproblems** and **optimal substructure**.

### Example:

- Fibonacci
    
- Knapsack
    
- Coin change
    
- DP on grids
    

DP stores results of subproblems → reduces exponential → polynomial time.

---

## **28. What is the greedy algorithm approach?**

Greedy picks **locally optimal choice** at each step hoping for global optimum.

### Common greedy problems:

- Activity selection
    
- Fractional knapsack
    
- Huffman coding
    

Greedy does NOT always give optimal results → only for specific structures (e.g., matroid).

---

## **29. What is memoization? How is it different from caching?**

### Memoization

- Technique for **storing results of expensive function calls**
    
- Usually used in recursion
    
- Keys are input parameters
    

### Caching

- Broader concept
    
- Stores frequently accessed data (DB results, API responses)
    
- Not necessarily tied to recursion
    

Memoization is a **type of caching**.

---

## **30. Why is time complexity more important than runtime in interviews?**

Because:

- Actual runtime depends on machine, compiler, input size
    
- Complexity reflects **scalability**
    
- Companies care how your solution works for large inputs