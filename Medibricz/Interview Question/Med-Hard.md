# Problem 1 — Two Sum (Brute force)

**Input:** `nums: List[int], target: int`  
**Output:** indices `[i, j]` such that `nums[i] + nums[j] == target` (any valid pair)

**What it is:** find two numbers in the array that add up to `target`.

**How to achieve (step-by-step):**

1. Try every possible pair of indices `(i, j)` with `i < j`.
    
2. For each pair, compute `nums[i] + nums[j]`.
    
3. If the sum equals `target`, return the pair of indices.
    
4. If no pair found, return an empty result or `null`.
    

**Why it works:** exhaustive search — guarantees finding a pair if one exists.  
**Complexity:** O(n²) time, O(1) extra space.

```python
# Python
def two_sum(nums, target):
    for i in range(len(nums)):
        for j in range(i+1, len(nums)):
            if nums[i] + nums[j] == target:
                return [i, j]
    return None
```

```javascript
// JavaScript
function twoSum(nums, target) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) return [i, j];
    }
  }
  return null;
}
```

```cpp
// C++ (STL)
#include <vector>
using namespace std;
vector<int> twoSum(vector<int>& nums, int target) {
    for (int i = 0; i < (int)nums.size(); ++i)
        for (int j = i+1; j < (int)nums.size(); ++j)
            if (nums[i] + nums[j] == target) return {i, j};
    return {};
}
```

```java
// Java
class Solution {
  public int[] twoSum(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
      for (int j = i+1; j < nums.length; j++) {
        if (nums[i] + nums[j] == target) return new int[]{i,j};
      }
    }
    return null;
  }
}
```

---

# Problem 2 — Two Sum (Faster: Hash Map)

**Input:** `nums: List[int], target: int`  
**Output:** indices `[i, j]` such that `nums[i] + nums[j] == target`

**What it is:** same task, but optimized.

**How to achieve (step-by-step):**

1. Create an empty hash map `value -> index`.
    
2. Iterate list with index `i` and value `v = nums[i]`.
    
3. Compute `need = target - v`.
    
4. If `need` exists in the map, we found indices `[map[need], i]`.
    
5. Otherwise store `map[v] = i` and continue.
    
6. This finds a pair in one pass.
    

**Why it works:** uses complement checking; map lookup is O(1) average.  
**Complexity:** O(n) time, O(n) space.

```python
# Python
def two_sum_hash(nums, target):
    seen = {}
    for i, v in enumerate(nums):
        need = target - v
        if need in seen:
            return [seen[need], i]
        seen[v] = i
    return None
```

```javascript
// JavaScript
function twoSumHash(nums, target) {
  const map = new Map();
  for (let i = 0; i < nums.length; i++) {
    const need = target - nums[i];
    if (map.has(need)) return [map.get(need), i];
    map.set(nums[i], i);
  }
  return null;
}
```

```cpp
// C++ (STL)
#include <vector>
#include <unordered_map>
using namespace std;
vector<int> twoSumHash(vector<int>& nums, int target) {
    unordered_map<int,int> mp;
    for (int i = 0; i < (int)nums.size(); ++i) {
        int need = target - nums[i];
        if (mp.count(need)) return {mp[need], i};
        mp[nums[i]] = i;
    }
    return {};
}
```

```java
// Java
import java.util.*;
class Solution {
  public int[] twoSumHash(int[] nums, int target) {
    Map<Integer,Integer> map = new HashMap<>();
    for (int i=0;i<nums.length;i++){
      int need = target - nums[i];
      if (map.containsKey(need)) return new int[]{map.get(need), i};
      map.put(nums[i], i);
    }
    return null;
  }
}
```

---

# Problem 3 — Move All Zeroes to End

**Input:** `nums: List[int]` (in-place modification expected)  
**Output:** same list with all zeros moved to the end, relative order of non-zero elements preserved

**What it is:** compact the non-zero elements to the front, append zeros after.

**How to achieve (step-by-step):**

1. Maintain `pos = 0` indicating next write position for non-zero.
    
2. Iterate elements:
    
    - If element `!= 0`, assign `nums[pos] = element` and `pos += 1`.
        
3. After loop, fill `nums[pos:]` with zeros until end.
    
4. This preserves the order of non-zero values and runs in-place.
    

**Why it works:** writes all non-zero elements in order to front, then fills remainder with zeros.  
**Complexity:** O(n) time, O(1) extra space.

```python
# Python
def move_zeroes(nums):
    pos = 0
    for x in nums:
        if x != 0:
            nums[pos] = x
            pos += 1
    while pos < len(nums):
        nums[pos] = 0
        pos += 1
    return nums
```

```javascript
// JavaScript
function moveZeroes(nums) {
  let pos = 0;
  for (let x of nums) if (x !== 0) nums[pos++] = x;
  while (pos < nums.length) nums[pos++] = 0;
  return nums;
}
```

```cpp
// C++ (STL)
#include <vector>
using namespace std;
vector<int> moveZeroes(vector<int>& nums) {
    int pos = 0;
    for (int x : nums) if (x != 0) nums[pos++] = x;
    while (pos < (int)nums.size()) nums[pos++] = 0;
    return nums;
}
```

```java
// Java
class Solution {
  public int[] moveZeroes(int[] nums) {
    int pos = 0;
    for (int x : nums) if (x != 0) nums[pos++] = x;
    while (pos < nums.length) nums[pos++] = 0;
    return nums;
  }
}
```

---

# Problem 4 — Longest Substring Without Repeating Characters

**Input:** `s: string`  
**Output:** length `int` of the longest substring with all unique characters

**What it is:** find the maximum-length contiguous substring with no repeated characters.

**How to achieve (step-by-step):**

1. Use a sliding window defined by indices `left` and `right`.
    
2. Use a map `lastSeen` to remember the last index of each character.
    
3. Move `right` forward one char at a time:
    
    - If current char `c` was last seen at index ≥ `left`, move `left` to `lastSeen[c] + 1` to avoid duplicates.
        
    - Update `lastSeen[c] = right`.
        
    - Update `best = max(best, right - left + 1)`.
        
4. Return `best`.
    

**Why it works:** window always contains unique characters; `left` jumps past duplicates, ensuring linear time.  
**Complexity:** O(n) time, O(min(n, alphabet)) space.

```python
# Python
def length_of_longest_substring(s):
    last = {}
    left = 0
    best = 0
    for right, ch in enumerate(s):
        if ch in last and last[ch] >= left:
            left = last[ch] + 1
        last[ch] = right
        best = max(best, right - left + 1)
    return best
```

```javascript
// JavaScript
function lengthOfLongestSubstring(s) {
  const last = new Map();
  let left = 0, best = 0;
  for (let right = 0; right < s.length; right++) {
    const ch = s[right];
    if (last.has(ch) && last.get(ch) >= left) left = last.get(ch) + 1;
    last.set(ch, right);
    best = Math.max(best, right - left + 1);
  }
  return best;
}
```

```cpp
// C++ (STL)
#include <string>
#include <unordered_map>
using namespace std;
int lengthOfLongestSubstring(const string& s) {
    unordered_map<char,int> last;
    int left = 0, best = 0;
    for (int right = 0; right < (int)s.size(); ++right) {
        char c = s[right];
        if (last.count(c) && last[c] >= left) left = last[c] + 1;
        last[c] = right;
        best = max(best, right - left + 1);
    }
    return best;
}
```

```java
// Java
import java.util.*;
class Solution {
  public int lengthOfLongestSubstring(String s) {
    Map<Character,Integer> last = new HashMap<>();
    int left = 0, best = 0;
    for (int right = 0; right < s.length(); right++) {
      char c = s.charAt(right);
      if (last.containsKey(c) && last.get(c) >= left) left = last.get(c) + 1;
      last.put(c, right);
      best = Math.max(best, right - left + 1);
    }
    return best;
  }
}
```

---

# Problem 5 — Merge Two Sorted Arrays

**Input:** two sorted arrays `a` and `b`  
**Output:** a new sorted array containing all elements from `a` and `b`

**What it is:** standard merge step of merge sort.

**How to achieve (step-by-step):**

1. Initialize pointers `i = 0`, `j = 0`, and `out = []`.
    
2. While both arrays have elements:
    
    - Compare `a[i]` and `b[j]`, append smaller to `out`, advance that pointer.
        
3. When one array is exhausted, append remaining elements of the other.
    
4. Return `out`.
    

**Why it works:** both inputs are sorted, so merging by always choosing the smaller next element produces a sorted result.  
**Complexity:** O(n + m) time, O(n + m) space.

```python
# Python
def merge_sorted(a, b):
    i = j = 0
    out = []
    while i < len(a) and j < len(b):
        if a[i] < b[j]:
            out.append(a[i]); i += 1
        else:
            out.append(b[j]); j += 1
    out.extend(a[i:]); out.extend(b[j:])
    return out
```

```javascript
// JavaScript
function mergeSorted(a, b) {
  let i = 0, j = 0, out = [];
  while (i < a.length && j < b.length) out.push(a[i] < b[j] ? a[i++] : b[j++]);
  return out.concat(a.slice(i)).concat(b.slice(j));
}
```

```cpp
// C++ (STL)
#include <vector>
using namespace std;
vector<int> mergeSorted(const vector<int>& a, const vector<int>& b) {
    vector<int> out; out.reserve(a.size() + b.size());
    int i = 0, j = 0;
    while (i < (int)a.size() && j < (int)b.size())
        out.push_back(a[i] < b[j] ? a[i++] : b[j++]);
    while (i < (int)a.size()) out.push_back(a[i++]);
    while (j < (int)b.size()) out.push_back(b[j++]);
    return out;
}
```

```java
// Java
import java.util.*;
class Solution {
  public int[] mergeSorted(int[] a, int[] b) {
    int i = 0, j = 0, k = 0;
    int[] out = new int[a.length + b.length];
    while (i < a.length && j < b.length) out[k++] = (a[i] < b[j]) ? a[i++] : b[j++];
    while (i < a.length) out[k++] = a[i++];
    while (j < b.length) out[k++] = b[j++];
    return out;
  }
}
```

---

# Problem 6 — Find Missing Number (0…n)

**Input:** array `nums` containing distinct numbers from `0..n` with exactly one missing; length is `n` (so numbers range 0..n, size n)  
**Output:** the missing number

**What it is:** find the one missing integer in the range.

**How to achieve (step-by-step):**

1. The sum of `0..n` is `n*(n+1)/2`.
    
2. Compute `expected = n*(n+1)//2` where `n = len(nums)`.
    
3. Subtract `sum(nums)` from `expected` → this gives the missing number.
    
4. Alternative: XOR approach `xor_all ^ xor_nums`.
    

**Why it works:** arithmetic identity or XOR cancelation.  
**Complexity:** O(n) time, O(1) space.

```python
# Python
def missing_number(nums):
    n = len(nums)
    expected = n * (n + 1) // 2
    return expected - sum(nums)
```

```javascript
// JavaScript
function missingNumber(nums) {
  const n = nums.length;
  const expected = (n * (n + 1)) / 2;
  return expected - nums.reduce((a,b)=>a+b, 0);
}
```

```cpp
// C++ (STL)
#include <vector>
using namespace std;
int missingNumber(const vector<int>& nums) {
    long long n = nums.size();
    long long expected = n * (n + 1) / 2;
    long long s = 0;
    for (int x : nums) s += x;
    return (int)(expected - s);
}
```

```java
// Java
class Solution {
  public int missingNumber(int[] nums) {
    int n = nums.length;
    int expected = n * (n + 1) / 2;
    int sum = 0;
    for (int x : nums) sum += x;
    return expected - sum;
  }
}
```

---

# Problem 7 — Valid Parentheses

**Input:** string `s` containing `()[]{}` characters  
**Output:** boolean `true` if parentheses are valid (properly nested and matched), else `false`

**What it is:** check balanced brackets.

**How to achieve (step-by-step):**

1. Use a stack.
    
2. Iterate characters:
    
    - If char is opening bracket `(`, `[`, `{` → push onto stack.
        
    - If char is closing bracket `)`, `]`, `}` → if stack empty or top not matching opening, return `false`; otherwise pop.
        
3. At end, return `true` if stack empty (all matched), else `false`.
    

**Why it works:** stack enforces LIFO matching for nested structures.  
**Complexity:** O(n) time, O(n) space.

```python
# Python
def is_valid_parentheses(s):
    stack = []
    pairs = {')':'(', ']':'[', '}':'{'}
    for ch in s:
        if ch in "([{":
            stack.append(ch)
        else:
            if not stack or stack.pop() != pairs.get(ch):
                return False
    return not stack
```

```javascript
// JavaScript
function isValid(s) {
  const stack = [];
  const pairs = {')':'(', ']':'[', '}':'{'};
  for (const ch of s) {
    if ("([{".includes(ch)) stack.push(ch);
    else {
      if (!stack.length || stack.pop() !== pairs[ch]) return false;
    }
  }
  return stack.length === 0;
}
```

```cpp
// C++ (STL)
#include <stack>
#include <string>
#include <unordered_map>
using namespace std;
bool isValidParentheses(const string& s) {
    stack<char> st;
    unordered_map<char,char> pairs = {{')','('},{']','['},{'}','{'}};
    for (char c : s) {
        if (c == '(' || c == '[' || c == '{') st.push(c);
        else {
            if (st.empty() || st.top() != pairs[c]) return false;
            st.pop();
        }
    }
    return st.empty();
}
```

```java
// Java
import java.util.*;
class Solution {
  public boolean isValidParentheses(String s) {
    Deque<Character> st = new ArrayDeque<>();
    Map<Character,Character> pairs = Map.of(')', '(', ']', '[', '}', '{');
    for (char c : s.toCharArray()) {
      if (c == '(' || c == '[' || c == '{') st.push(c);
      else {
        if (st.isEmpty() || st.pop() != pairs.get(c)) return false;
      }
    }
    return st.isEmpty();
  }
}
```

---

# Problem 8 — Find Majority Element (> n/2 occurrences)

**Input:** array `nums` of length n where a majority element (occurring > n/2) is guaranteed (or not guaranteed depending on variant)  
**Output:** the majority element

**What it is:** find element appearing more than half of the array length.

**How to achieve (step-by-step — Boyer-Moore Voting):**

1. Initialize `candidate = None`, `count = 0`.
    
2. For each number `x`:
    
    - If `count == 0`, set `candidate = x` and `count = 1`.
        
    - Else if `x == candidate`, `count += 1`.
        
    - Else `count -= 1`.
        
3. After one pass, `candidate` is the majority (if one exists). Optionally verify in a second pass that it occurs > n/2.
    

**Why it works:** pairs of different elements cancel out; majority remains.  
**Complexity:** O(n) time, O(1) space.

```python
# Python
def majority_element(nums):
    candidate, count = None, 0
    for x in nums:
        if count == 0:
            candidate, count = x, 1
        elif x == candidate:
            count += 1
        else:
            count -= 1
    return candidate
```

```javascript
// JavaScript
function majorityElement(nums) {
  let cand = null, count = 0;
  for (const x of nums) {
    if (count === 0) { cand = x; count = 1; }
    else if (x === cand) count++;
    else count--;
  }
  return cand;
}
```

```cpp
// C++ (STL)
#include <vector>
using namespace std;
int majorityElement(const vector<int>& nums) {
    int cand = 0, cnt = 0;
    for (int x : nums) {
        if (cnt == 0) { cand = x; cnt = 1; }
        else if (x == cand) ++cnt;
        else --cnt;
    }
    return cand;
}
```

```java
// Java
class Solution {
  public int majorityElement(int[] nums) {
    int cand = 0, cnt = 0;
    for (int x : nums) {
      if (cnt == 0) { cand = x; cnt = 1; }
      else if (x == cand) cnt++;
      else cnt--;
    }
    return cand;
  }
}
```

---

# Problem 9 — Binary Search on Rotated Sorted Array

**Input:** `nums: rotated sorted array`, `target: int`  
**Output:** index of `target` or `-1` if not found

**What it is:** array originally sorted ascending was rotated at some pivot; find target index efficiently.

**How to achieve (step-by-step):**

1. Use modified binary search with `l` and `r`.
    
2. At middle `m`:
    
    - If `nums[m] == target`, return `m`.
        
    - Determine which half is sorted:
        
        - If `nums[l] <= nums[m]` → left half is sorted.
            
            - If `nums[l] <= target < nums[m]` → search left (`r = m - 1`).
                
            - Else search right (`l = m + 1`).
                
        - Else right half is sorted:
            
            - If `nums[m] < target <= nums[r]` → search right (`l = m + 1`).
                
            - Else search left.
                
3. Repeat until `l > r`.
    

**Why it works:** one half is always sorted; target must be in either the sorted half within bounds or in the other half; reduces to regular binary decisions.  
**Complexity:** O(log n) time.

```python
# Python
def search_rotated(nums, target):
    l, r = 0, len(nums) - 1
    while l <= r:
        m = (l + r) // 2
        if nums[m] == target: return m
        if nums[l] <= nums[m]:
            if nums[l] <= target < nums[m]: r = m - 1
            else: l = m + 1
        else:
            if nums[m] < target <= nums[r]: l = m + 1
            else: r = m - 1
    return -1
```

```javascript
// JavaScript
function searchRotated(nums, target) {
  let l = 0, r = nums.length - 1;
  while (l <= r) {
    const m = Math.floor((l + r) / 2);
    if (nums[m] === target) return m;
    if (nums[l] <= nums[m]) {
      if (nums[l] <= target && target < nums[m]) r = m - 1;
      else l = m + 1;
    } else {
      if (nums[m] < target && target <= nums[r]) l = m + 1;
      else r = m - 1;
    }
  }
  return -1;
}
```

```cpp
// C++ (STL)
#include <vector>
using namespace std;
int searchRotated(const vector<int>& nums, int target) {
    int l = 0, r = (int)nums.size() - 1;
    while (l <= r) {
        int m = (l + r) / 2;
        if (nums[m] == target) return m;
        if (nums[l] <= nums[m]) {
            if (nums[l] <= target && target < nums[m]) r = m - 1;
            else l = m + 1;
        } else {
            if (nums[m] < target && target <= nums[r]) l = m + 1;
            else r = m - 1;
        }
    }
    return -1;
}
```

```java
// Java
class Solution {
  public int searchRotated(int[] nums, int target) {
    int l = 0, r = nums.length - 1;
    while (l <= r) {
      int m = (l + r) / 2;
      if (nums[m] == target) return m;
      if (nums[l] <= nums[m]) {
        if (nums[l] <= target && target < nums[m]) r = m - 1;
        else l = m + 1;
      } else {
        if (nums[m] < target && target <= nums[r]) l = m + 1;
        else r = m - 1;
      }
    }
    return -1;
  }
}
```

---

# Problem 10 — Kth Largest Element

**Input:** array `nums`, integer `k` (1-based: 1 → largest)  
**Output:** the value of the k-th largest element

**What it is:** find the element that would be at index `n-k` if sorted ascending.

**How to achieve (step-by-step, using min-heap):**

1. Maintain a min-heap of size at most `k`.
    
2. Iterate over numbers:
    
    - Push number into heap.
        
    - If heap size > k, pop smallest (keeps heap containing k largest numbers seen).
        
3. After iteration, heap root (`top`) is the k-th largest.
    
4. This is efficient when k much smaller than n.
    

**Why it works:** the heap retains the k largest elements; smallest among them is the k-th largest overall.  
**Complexity:** O(n log k) time, O(k) space.

```python
# Python
import heapq
def kth_largest(nums, k):
    h = []
    for x in nums:
        heapq.heappush(h, x)
        if len(h) > k:
            heapq.heappop(h)
    return h[0]
```

```javascript
// JavaScript (uses array as simple sorted container; for large n use a proper heap lib)
function kthLargest(nums, k) {
  const heap = [];
  for (const x of nums) {
    heap.push(x);
    heap.sort((a,b)=>a-b);
    if (heap.length > k) heap.shift();
  }
  return heap[0];
}
```

```cpp
// C++ (STL)
#include <queue>
#include <vector>
using namespace std;
int kthLargest(const vector<int>& nums, int k) {
    priority_queue<int, vector<int>, greater<int>> pq;
    for (int x : nums) {
        pq.push(x);
        if ((int)pq.size() > k) pq.pop();
    }
    return pq.top();
}
```

```java
// Java
import java.util.*;
class Solution {
  public int kthLargest(int[] nums, int k) {
    PriorityQueue<Integer> pq = new PriorityQueue<>();
    for (int x : nums) {
      pq.add(x);
      if (pq.size() > k) pq.poll();
    }
    return pq.peek();
  }
}
```

---

# Problem 11 — Count Pairs With Given Sum

**Input:** array `nums`, integer `target`  
**Output:** number of pairs `(i, j)` (i < j) such that `nums[i] + nums[j] == target` — counts duplicates appropriately

**What it is:** count unordered pairs summing to a target.

**How to achieve (step-by-step):**

1. Use a hashmap `count[value]` to record how many times we've seen a value so far.
    
2. Iterate each `x` in `nums`:
    
    - Let `need = target - x`.
        
    - If `need` present in `count`, increment `result` by `count[need]` (each previous occurrence forms pairs with current x).
        
    - Then increment `count[x]`.
        
3. End: `result` is total pairs.
    

**Why it works:** counts complement occurrences seen earlier; avoids double counting by only pairing current with earlier elements.  
**Complexity:** O(n) time, O(n) space.

```python
# Python
def count_pairs(nums, target):
    counts = {}
    res = 0
    for x in nums:
        need = target - x
        res += counts.get(need, 0)
        counts[x] = counts.get(x, 0) + 1
    return res
```

```javascript
// JavaScript
function countPairs(nums, target) {
  const map = Object.create(null);
  let res = 0;
  for (const x of nums) {
    const need = target - x;
    if (map[need]) res += map[need];
    map[x] = (map[x] || 0) + 1;
  }
  return res;
}
```

```cpp
// C++ (STL)
#include <vector>
#include <unordered_map>
using namespace std;
long long countPairs(const vector<int>& nums, int target) {
    unordered_map<int,long long> cnt;
    long long res = 0;
    for (int x : nums) {
        int need = target - x;
        if (cnt.count(need)) res += cnt[need];
        cnt[x]++;
    }
    return res;
}
```

```java
// Java
import java.util.*;
class Solution {
  public long countPairs(int[] nums, int target) {
    Map<Integer, Long> map = new HashMap<>();
    long res = 0;
    for (int x : nums) {
      int need = target - x;
      res += map.getOrDefault(need, 0L);
      map.put(x, map.getOrDefault(x, 0L) + 1);
    }
    return res;
  }
}
```

---

# Problem 12 — Convert text to lowercase and remove punctuation

**Input:** string `text`  
**Output:** cleaned string with lowercase letters and digits and spaces only

**What it is:** normalization for basic text processing.

**How to achieve (step-by-step):**

1. Convert the string to lowercase.
    
2. Remove any character that is not a letter (`a-z`), digit (`0-9`), or space.
    
    - Use regex replacement or iterate and filter characters.
        
3. Return cleaned text.
    

**Why it works:** keeps only tokenizable characters; punctuation removed for simpler token counts or search.  
**Complexity:** O(n) time.

```python
# Python
import re
def clean_text(text):
    text = text.lower()
    # remove anything that's not a lowercase letter, digit or space
    return re.sub(r'[^a-z0-9 ]+', '', text)
```

```javascript
// JavaScript
function cleanText(text) {
  return text.toLowerCase().replace(/[^a-z0-9 ]+/g, '');
}
```

```cpp
// C++ (STL)
#include <string>
using namespace std;
string cleanText(const string& s) {
    string out;
    out.reserve(s.size());
    for (char c : s) {
        if (isalnum((unsigned char)c) || c == ' ') out.push_back(tolower((unsigned char)c));
    }
    return out;
}
```

```java
// Java
class TextUtils {
  public static String cleanText(String s) {
    s = s.toLowerCase();
    return s.replaceAll("[^a-z0-9 ]+", "");
  }
}
```

---

# Problem 13 — Token Count

**Input:** string `s` (e.g. `"AI will change the world"`)  
**Output:** integer number of tokens (words) — here `5`

**What it is:** count words separated by whitespace.

**How to achieve (step-by-step):**

1. Trim leading/trailing whitespace.
    
2. If empty string → 0.
    
3. Split on one-or-more whitespace (`\s+`) and count tokens.
    

**Why it works:** tokens are contiguous non-space sequences.  
**Complexity:** O(n) time.

```python
# Python
def token_count(s):
    s = s.strip()
    if not s: return 0
    return len(s.split())
# Example: token_count("AI will change the world") -> 5
```

```javascript
// JavaScript
function tokenCount(s) {
  s = s.trim();
  if (!s) return 0;
  return s.split(/\s+/).length;
}
```

```cpp
// C++ (STL)
#include <sstream>
#include <string>
using namespace std;
int tokenCount(const string& s) {
    istringstream iss(s);
    string w; int c = 0;
    while (iss >> w) ++c;
    return c;
}
```

```java
// Java
class Solution {
  public int tokenCount(String s) {
    s = s.trim();
    if (s.isEmpty()) return 0;
    return s.split("\\s+").length;
  }
}
```

---

# Problem 14 — Rate Limiter: Allow 1 request every 2 seconds

**Input:** timestamps (integers) e.g. `[1,1,2,2,4]`  
**Output:** list of `ALLOW` or `BLOCK` decisions per timestamp → `["ALLOW","BLOCK","ALLOW","BLOCK","ALLOW"]`

**What it is:** enforce a simple rate: at most one allowed request for each 2-second window; window is measured relative to last allowed request.

**How to achieve (step-by-step):**

1. Keep `last_allowed_time = -infinity` (or a sentinel).
    
2. For each timestamp `t`:
    
    - If `t - last_allowed_time >= 2`, mark `ALLOW`, set `last_allowed_time = t`.
        
    - Else mark `BLOCK`.
        
3. Return decisions.
    

**Why it works:** enforces a fixed minimum spacing between allowed requests.  
**Complexity:** O(n) time.

```python
# Python
def rate_limiter(timestamps, interval=2):
    result = []
    last_allowed = -10**9
    for t in timestamps:
        if t - last_allowed >= interval:
            result.append("ALLOW")
            last_allowed = t
        else:
            result.append("BLOCK")
    return result

# Example:
# rate_limiter([1,1,2,2,4]) -> ["ALLOW","BLOCK","ALLOW","BLOCK","ALLOW"]
```

```javascript
// JavaScript
function rateLimiter(timestamps, interval = 2) {
  const out = [];
  let lastAllowed = -1e9;
  for (const t of timestamps) {
    if (t - lastAllowed >= interval) { out.push("ALLOW"); lastAllowed = t; }
    else out.push("BLOCK");
  }
  return out;
}
```

```cpp
// C++ (STL)
#include <vector>
#include <string>
using namespace std;
vector<string> rateLimiter(const vector<int>& ts, int interval=2) {
    vector<string> out; out.reserve(ts.size());
    int last = -1000000000;
    for (int t : ts) {
        if (t - last >= interval) { out.push_back("ALLOW"); last = t; }
        else out.push_back("BLOCK");
    }
    return out;
}
```

```java
// Java
import java.util.*;
class Solution {
  public List<String> rateLimiter(int[] ts, int interval) {
    List<String> out = new ArrayList<>();
    int last = Integer.MIN_VALUE / 2;
    for (int t : ts) {
      if (t - last >= interval) { out.add("ALLOW"); last = t; }
      else out.add("BLOCK");
    }
    return out;
  }
}
```

---

# Problem 15 — Cache Simulation (LRU) — count cache hits

**Input:** key accesses (e.g. `['a','b','a','c','a','b','a']`), cache size (e.g. `2`)  
**Output:** integer number of cache hits

**What it is:** simulate an LRU cache of fixed size; count how many accesses hit the cache (already present).

**How to achieve (step-by-step):**

1. Use an ordered container representing cache from least-recently-used (LRU) to most-recently-used (MRU).
    
2. For each access `k`:
    
    - If `k` in cache → it's a hit: increment `hits`, update `k` to MRU position (remove old, append new).
        
    - Else miss: if cache full remove LRU item; insert `k` as MRU.
        
3. Return `hits`.
    

**Why it works:** LRU eviction ensures the least recently used key is removed when capacity reached.  
**Complexity:** O(n * cost_lookup). With an ordered hash structure (linked hash or list+map) you can achieve O(1) per access; the simple list/indexOf solution costs O(size) per lookup.

```python
# Python (simple list implementation)
def cache_hits(accesses, size=2):
    cache = []
    hits = 0
    for k in accesses:
        if k in cache:
            hits += 1
            cache.remove(k)
            cache.append(k)
        else:
            if len(cache) == size:
                cache.pop(0)
            cache.append(k)
    return hits

# Example:
# cache_hits(['a','b','a','c','a','b','a'], 2) -> 3 (hits at accesses #3, #5, #7)
```

```javascript
// JavaScript
function cacheHits(accesses, size = 2) {
  const cache = [];
  let hits = 0;
  for (const k of accesses) {
    const idx = cache.indexOf(k);
    if (idx !== -1) {
      hits++;
      cache.splice(idx, 1);
      cache.push(k);
    } else {
      if (cache.length === size) cache.shift();
      cache.push(k);
    }
  }
  return hits;
}
```

```cpp
// C++ (STL) — using list + find (simple)
#include <list>
#include <vector>
using namespace std;
int cacheHits(const vector<char>& acc, int size = 2) {
    list<char> cache;
    int hits = 0;
    for (char k : acc) {
        auto it = find(cache.begin(), cache.end(), k);
        if (it != cache.end()) {
            ++hits;
            cache.erase(it);
            cache.push_back(k);
        } else {
            if ((int)cache.size() == size) cache.pop_front();
            cache.push_back(k);
        }
    }
    return hits;
}
```

```java
// Java
import java.util.*;
class Solution {
  public int cacheHits(char[] acc, int size) {
    LinkedList<Character> cache = new LinkedList<>();
    int hits = 0;
    for (char k : acc) {
      if (cache.contains(k)) {
        hits++;
        cache.remove((Character)k);
        cache.add(k);
      } else {
        if (cache.size() == size) cache.removeFirst();
        cache.add(k);
      }
    }
    return hits;
  }
}
```

---

# Problem 16 — Merge Overlapping Time Intervals

**Input:** list of intervals `[(start,end), ...]` (unsorted)  
**Output:** merged list with overlapping intervals combined

**What it is:** given intervals, combine overlapping ones into minimal set of disjoint intervals.

**How to achieve (step-by-step):**

1. Sort intervals by `start`.
    
2. Initialize `merged` with first interval.
    
3. For each subsequent interval `(s, e)`:
    
    - Let `last = merged[-1]`.
        
    - If `s <= last.end` → overlap: set `last.end = max(last.end, e)`.
        
    - Else → no overlap: append `(s, e)` to `merged`.
        
4. Return `merged`.
    

**Why it works:** sorted starts ensure any overlap must be with the last merged interval.  
**Complexity:** O(n log n) due to sorting, O(n) merge pass.

```python
# Python
def merge_intervals(intervals):
    if not intervals: return []
    intervals.sort(key=lambda x: x[0])
    merged = [intervals[0][:]]
    for s, e in intervals[1:]:
        last = merged[-1]
        if s <= last[1]:
            last[1] = max(last[1], e)
        else:
            merged.append([s, e])
    return merged

# Example:
# merge_intervals([[1,3],[2,6],[8,10]]) -> [[1,6],[8,10]]
```

```javascript
// JavaScript
function mergeIntervals(intervals) {
  if (!intervals.length) return [];
  intervals.sort((a,b) => a[0] - b[0]);
  const out = [intervals[0].slice()];
  for (let i = 1; i < intervals.length; i++) {
    const [s, e] = intervals[i];
    const last = out[out.length - 1];
    if (s <= last[1]) last[1] = Math.max(last[1], e);
    else out.push([s, e]);
  }
  return out;
}
```

```cpp
// C++ (STL)
#include <vector>
#include <algorithm>
using namespace std;
vector<vector<int>> mergeIntervals(vector<vector<int>>& intervals) {
    if (intervals.empty()) return {};
    sort(intervals.begin(), intervals.end());
    vector<vector<int>> out;
    out.push_back(intervals[0]);
    for (int i = 1; i < (int)intervals.size(); ++i) {
        auto &last = out.back();
        if (intervals[i][0] <= last[1]) last[1] = max(last[1], intervals[i][1]);
        else out.push_back(intervals[i]);
    }
    return out;
}
```

```java
// Java
import java.util.*;
class Solution {
  public int[][] mergeIntervals(int[][] intervals) {
    if (intervals.length == 0) return new int[0][];
    Arrays.sort(intervals, Comparator.comparingInt(a -> a[0]));
    List<int[]> out = new ArrayList<>();
    out.add(intervals[0].clone());
    for (int i = 1; i < intervals.length; i++) {
      int[] last = out.get(out.size() - 1);
      if (intervals[i][0] <= last[1]) last[1] = Math.max(last[1], intervals[i][1]);
      else out.add(intervals[i].clone());
    }
    return out.toArray(new int[out.size()][]);
  }
}
```

---

# Problem 17 — Matrix Row Sum

**Input:** matrix `m x n` (list of rows)  
**Output:** array of row sums

**What it is:** for each row compute the sum of its elements.

**How to achieve (step-by-step):**

1. For each row, iterate elements and accumulate sum.
    
2. Save result for that row.
    
3. Return array of sums.
    

**Why it works:** direct aggregation per row.  
**Complexity:** O(m*n) time.

```python
# Python
def row_sums(matrix):
    return [sum(row) for row in matrix]
```

```javascript
// JavaScript
function rowSums(matrix) {
  return matrix.map(row => row.reduce((a,b) => a + b, 0));
}
```

```cpp
// C++ (STL)
#include <vector>
using namespace std;
vector<int> rowSums(const vector<vector<int>>& mat) {
    vector<int> out;
    out.reserve(mat.size());
    for (const auto& row : mat) {
        int s = 0;
        for (int x : row) s += x;
        out.push_back(s);
    }
    return out;
}
```

```java
// Java
import java.util.*;
class Solution {
  public int[] rowSums(int[][] mat) {
    int[] out = new int[mat.length];
    for (int i = 0; i < mat.length; i++) {
      int s = 0;
      for (int x : mat[i]) s += x;
      out[i] = s;
    }
    return out;
  }
}
```

---

# Problem 18 — Flatten Nested List

**Input:** nested list of integers, e.g. `[1,[2,3],[4,[5]]]` (heterogeneous nested arrays)  
**Output:** flat list of integers `[1,2,3,4,5]`

**What it is:** recursively expand sublists into a flat sequence.

**How to achieve (step-by-step):**

1. Initialize an output list.
    
2. Iterate over items:
    
    - If item is an integer → append to output.
        
    - If item is a list/array → recursively flatten it and extend output with result.
        
3. Return output.
    

**Why it works:** recursion processes arbitrarily nested lists depth-first.  
**Complexity:** O(total number of elements) time.

```python
# Python
def flatten(lst):
    out = []
    for x in lst:
        if isinstance(x, list):
            out.extend(flatten(x))
        else:
            out.append(x)
    return out

# Example:
# flatten([1,[2,3],[4,[5]]]) -> [1,2,3,4,5]
```

```javascript
// JavaScript
function flatten(arr) {
  const out = [];
  for (const x of arr) {
    if (Array.isArray(x)) out.push(...flatten(x));
    else out.push(x);
  }
  return out;
}
```

```cpp
// C++ (STL) — representation in C++ is more complex; here is conceptual recursion if nested as vectors of variants.
// For interviews, explain approach and implement in language with native nested lists (Python/JS/Java).
```

```java
// Java
import java.util.*;
class Solution {
  public List<Integer> flatten(Object[] arr) {
    List<Integer> out = new ArrayList<>();
    for (Object x : arr) {
      if (x instanceof Object[]) out.addAll(flatten((Object[]) x));
      else out.add((Integer) x);
    }
    return out;
  }
}
```

---

# Problem 19 — Batching Logic (Split into batches of size 3)

**Input:** list `arr`, batch size `k` (default 3)  
**Output:** list of batches (lists), last batch may be shorter

**What it is:** partition array into consecutive chunks of size `k`.

**How to achieve (step-by-step):**

1. Iterate `i` from 0 to `len(arr)` stepping by `k`.
    
2. Slice `arr[i : i + k]` and add to output.
    
3. Continue until consumed.
    

**Why it works:** slicing in fixed windows partitions the list.  
**Complexity:** O(n) time.

```python
# Python
def batchify(arr, k=3):
    return [arr[i:i+k] for i in range(0, len(arr), k)]
# Example: batchify([1,2,3,4,5,6,7],3) -> [[1,2,3],[4,5,6],[7]]
```

```javascript
// JavaScript
function batchify(arr, k = 3) {
  const out = [];
  for (let i = 0; i < arr.length; i += k) out.push(arr.slice(i, i + k));
  return out;
}
```

```cpp
// C++ (STL)
#include <vector>
using namespace std;
vector<vector<int>> batchify(const vector<int>& arr, int k = 3) {
    vector<vector<int>> out;
    for (int i = 0; i < (int)arr.size(); i += k) {
        vector<int> b;
        for (int j = i; j < min((int)arr.size(), i + k); ++j) b.push_back(arr[j]);
        out.push_back(b);
    }
    return out;
}
```

```java
// Java
import java.util.*;
class Solution {
  public List<List<Integer>> batchify(int[] arr, int k) {
    List<List<Integer>> out = new ArrayList<>();
    for (int i = 0; i < arr.length; i += k) {
      List<Integer> b = new ArrayList<>();
      for (int j = i; j < Math.min(arr.length, i + k); j++) b.add(arr[j]);
      out.add(b);
    }
    return out;
  }
}
```

---

# Problem 20 — Frequency Map

**Input:** string `s` (e.g. `"banana"`)  
**Output:** mapping of character → count, e.g. `{ 'b':1, 'a':3, 'n':2 }`

**What it is:** count occurrences of each character.

**How to achieve (step-by-step):**

1. Create an empty dictionary/map `count`.
    
2. Iterate characters `c` in `s`: `count[c] = count.get(c, 0) + 1`.
    
3. Return `count`.
    

**Why it works:** simple accumulation per key.  
**Complexity:** O(n) time, O(k) space (k = distinct chars).

```python
# Python
def frequency_map(s):
    d = {}
    for ch in s:
        d[ch] = d.get(ch, 0) + 1
    return d
# Example:
# frequency_map("banana") -> {'b':1, 'a':3, 'n':2}
```

```javascript
// JavaScript
function frequencyMap(s) {
  const map = Object.create(null);
  for (const ch of s) map[ch] = (map[ch] || 0) + 1;
  return map;
}
```

```cpp
// C++ (STL)
#include <unordered_map>
#include <string>
using namespace std;
unordered_map<char,int> frequencyMap(const string& s) {
    unordered_map<char,int> mp;
    for (char c : s) mp[c]++;
    return mp;
}
```

```java
// Java
import java.util.*;
class Solution {
  public Map<Character,Integer> frequencyMap(String s) {
    Map<Character,Integer> map = new HashMap<>();
    for (char c : s.toCharArray()) map.put(c, map.getOrDefault(c, 0) + 1);
    return map;
  }
}
```