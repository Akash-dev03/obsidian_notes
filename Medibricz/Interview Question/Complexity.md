**What is Time Complexity?**

Time Complexity describes **how the running time of an algorithm increases with input size (n)**.

It does NOT measure actual time.  
It measures **growth rate** when input becomes large.

### Example

If an algorithm takes:

- 1 second for n = 1000
    
- 2 seconds for n = 2000
    

Its runtime roughly doubles → O(n).

Time complexity lets you know **how well the algorithm scales**.

---

# 📘 **Why Do We Use Big-O?**

Big-O gives:

- Worst-case guarantee
    
- Machine-independent comparison
    
- Mathematical form of efficiency
    

Example:  
O(n²) is always slower than O(n log n) for very large n.

---

# 🧠 **Common Time Complexities (From Best to Worst)**

|Complexity|Name|Example|
|---|---|---|
|**O(1)**|Constant|Hashmap access|
|**O(log n)**|Logarithmic|Binary search|
|**O(n)**|Linear|Scanning a list|
|**O(n log n)**|Linearithmic|Merge sort|
|**O(n²)**|Quadratic|Nested loops|
|**O(2ⁿ)**|Exponential|Subset generation|
|**O(n!)**|Factorial|Travelling salesman|

---

# 🧩 **Graphical Intuition**

Fastest → Slowest:

O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) < O(n!)

---

# 🔍 **Examples**

### O(1)

Accessing arr[5] → always constant time.

### O(n)

Loop through an array once.

### O(n²)

Two nested loops scanning matrix.

### O(log n)

Binary search → cuts search space in half.

### O(n log n)

Divide & conquer sorting like merge sort.

---

# 📦 **What is Space Complexity?**

Space Complexity measures **extra memory** used by an algorithm (not the input).

It includes:

- Variables
    
- Data structures
    
- Recursion stack
    
- Auxiliary arrays
    

### Example

Merge sort uses **temporary arrays** → O(n) space.  
QuickSort uses **recursion** → O(log n) space average.

---

# 🧠 **Common Space Complexities**

|Space|Meaning|Example|
|---|---|---|
|**O(1)**|Constant|In-place algorithms|
|**O(log n)**|Log deep recursion|Balanced tree DFS|
|**O(n)**|Linear extra storage|BFS queue, prefix sums|
|**O(n²)**|2D arrays|DP matrix, adjacency matrix|

---

# 🎯 **TIME & SPACE COMPLEXITY EXAMPLES**

Here are famous algorithms with exact complexities.

---

# 🔥 **FAMOUS ALGO COMPLEXITIES**

---

# 🟦 **Searching Algorithms**

|Algorithm|Time|Space|
|---|---|---|
|Linear Search|**O(n)**|O(1)|
|Binary Search|**O(log n)**|O(1)|
|Hash Table Search|**O(1)** average, **O(n)** worst|O(n)|

---

# 🟪 **Sorting Algorithms**

|Algorithm|Best|Average|Worst|Space|
|---|---|---|---|---|
|**Bubble Sort**|O(n)|O(n²)|O(n²)|O(1)|
|**Selection Sort**|O(n²)|O(n²)|O(n²)|O(1)|
|**Insertion Sort**|O(n)|O(n²)|O(n²)|O(1)|
|**Merge Sort**|O(n log n)|O(n log n)|O(n log n)|O(n)|
|**QuickSort**|O(n log n)|O(n log n)|**O(n²)**|O(log n)|
|**HeapSort**|O(n log n)|O(n log n)|O(n log n)|O(1)|
|**Counting Sort**|O(n+k)|O(n+k)|O(n+k)|O(k)|
|**Radix Sort**|O(nk)|O(nk)|O(nk)|O(n+k)|

---

# 🟩 **Graph Algorithms**

|Algorithm|Time|Space|
|---|---|---|
|BFS|O(V + E)|O(V)|
|DFS|O(V + E)|O(V)|
|Dijkstra (Min-Heap)|O((V+E) log V)|O(V)|
|Bellman-Ford|O(V × E)|O(V)|
|Floyd–Warshall|O(V³)|O(V²)|
|Topological Sort|O(V+E)|O(V)|

---

# 🟥 **Tree Algorithms**

|Operation|Average Time|Worst Time|
|---|---|---|
|Search BST|O(log n)|O(n)|
|Insert BST|O(log n)|O(n)|
|Balanced BST (AVL/Red-Black)|O(log n)|O(log n)|
|Tree Traversals|O(n)|O(n)|

---

# 🟨 **Dynamic Programming**

|Problem|Time|Space|
|---|---|---|
|Fibonacci DP|O(n)|O(n) or O(1)|
|LCS|O(n × m)|O(n × m)|
|Knapsack|O(n × W)|O(n × W)|
|Edit Distance|O(n × m)|O(n × m)|

---

# 🟧 **Greedy Algorithms**

|Algorithm|Time|Space|
|---|---|---|
|Activity Selection|O(n log n)|O(1)|
|Huffman Coding|O(n log n)|O(n)|
|Kruskal’s MST|O(E log E)|O(V)|
|Prim’s MST (heap)|O(E log V)|O(V)|

---

# 🟫 **Hashing**

|Operation|Average|Worst|
|---|---|---|
|Insert|O(1)|O(n)|
|Search|O(1)|O(n)|
|Delete|O(1)|O(n)|

Worst-case occurs when all keys collide into one bucket.

---

# 🟪 **Famous Examples Summarized**

### BEST COMPLEXITIES

- Hashing: **O(1)**
    
- Binary Search: **O(log n)**
    
- Merge Sort / Heap Sort: **O(n log n)**
    

### WORST COMPLEXITIES

- QuickSort: **O(n²)**
    
- Bellman-Ford: **O(V × E)**
    
- Floyd-Warshall: **O(V³)**
    
- Travelling Salesman (exact): **O(n!)**
    

---

# 📜 **SHORT SUMMARY FOR INTERVIEWERS**

- Time Complexity → **growth of execution time**
    
- Space Complexity → **extra memory used**
    
- Big-O → **worst-case behavior**
    
- Good algorithms scale as:  
    **O(1) → O(log n) → O(n) → O(n log n)**
    
- Avoid **O(n²)** for large n
    
- Avoid **O(2ⁿ)** and **O(n!)** unless input is tiny