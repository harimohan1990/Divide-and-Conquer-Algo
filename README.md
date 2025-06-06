# Divide-and-Conquer-Algo

**Divide and Conquer Algorithm**

### 💡 **Definition**

Divide and Conquer is a strategy where a problem is divided into smaller subproblems, each subproblem is solved independently (often recursively), and then the solutions are combined to solve the original problem.

---

### 🔧 **Steps**

1. **Divide**: Break the problem into smaller subproblems.
2. **Conquer**: Solve each subproblem recursively.
3. **Combine**: Merge the solutions of the subproblems.

---

### 🔁 **Common Examples**

| Problem                            | Description                             |
| ---------------------------------- | --------------------------------------- |
| Merge Sort                         | Divide array, sort halves, then merge   |
| Quick Sort                         | Partition array, sort parts recursively |
| Binary Search                      | Divide array to find target efficiently |
| Maximum Subarray (Kadane’s)        | Divide into halves and combine results  |
| Matrix Multiplication (Strassen’s) | Break into smaller matrices             |

---

### 🧠 **Time Complexity Example**

**Merge Sort:**

* T(n) = 2T(n/2) + O(n)
* ⇒ T(n) = O(n log n)

Here’s a **complete deep dive into Divide and Conquer** — covering **concepts, math, applications, optimizations, patterns, and pitfalls**.

---

## 📌 1. What is Divide and Conquer?

It’s a **problem-solving paradigm** where a problem is:

* **Divided** into smaller subproblems of the same type,
* Each subproblem is **solved recursively**,
* Their results are **combined** to form the final output.

---

## 🧠 2. The 3 Fundamental Steps

| Step        | Description                                                      |
| ----------- | ---------------------------------------------------------------- |
| **Divide**  | Break the problem into smaller subproblems (often halves).       |
| **Conquer** | Solve subproblems **recursively** (or directly if small enough). |
| **Combine** | Merge subproblem solutions into a full solution.                 |

---

## 🧮 3. Master Theorem (Time Complexity Formula)

For recurrences of the form:

```
T(n) = aT(n/b) + O(n^d)
```

Where:

* `a` = number of subproblems,
* `n/b` = size of each subproblem,
* `O(n^d)` = cost of divide/combine.

**Result:**

| Case | Condition     | Complexity            |
| ---- | ------------- | --------------------- |
| 1    | d < log\_b(a) | T(n) = Θ(n^log\_b(a)) |
| 2    | d = log\_b(a) | T(n) = Θ(n^d · log n) |
| 3    | d > log\_b(a) | T(n) = Θ(n^d)         |

**Example:**
Merge Sort
T(n) = 2T(n/2) + O(n) → log₂(2) = 1 = d → **T(n) = O(n log n)**

---

## 💡 4. Classic Examples

| Problem                  | Divide          | Conquer          | Combine            | Time                        |
| ------------------------ | --------------- | ---------------- | ------------------ | --------------------------- |
| Merge Sort               | Split array     | Sort halves      | Merge              | O(n log n)                  |
| Quick Sort               | Partition       | Sort subarrays   | None               | Avg O(n log n), Worst O(n²) |
| Binary Search            | Middle of array | Choose side      | None               | O(log n)                    |
| Closest Pair (2D)        | Split on x-axis | Find min dist    | Compare split zone | O(n log n)                  |
| Karatsuba Multiplication | Split numbers   | Multiply parts   | Merge products     | O(n^1.58)                   |
| Strassen Matrix Mult.    | Split matrices  | Multiply 7 parts | Reconstruct        | O(n^2.81)                   |

---

## ⚙️ 5. Code Pattern (Generic Template in JS/TS)

```ts
function divideAndConquer(input): Result {
  if (isBaseCase(input)) return solveBase(input);

  const [left, right] = divide(input);

  const leftResult = divideAndConquer(left);
  const rightResult = divideAndConquer(right);

  return combine(leftResult, rightResult);
}
```

---

## 🧪 6. Optimizations

* **Tail recursion optimization** (if supported).
* **Memoization** to store overlapping subproblem results.
* **Hybrid approaches**: switch to brute force for small subproblem sizes.
* **Parallel execution**: subproblems solved concurrently using threads/cores.

---

## 🧱 7. Divide and Conquer vs Dynamic Programming

| Feature              | Divide and Conquer        | Dynamic Programming      |
| -------------------- | ------------------------- | ------------------------ |
| Subproblem Overlap   | No (typically)            | Yes                      |
| Optimal Substructure | Yes                       | Yes                      |
| Memoization          | Rarely used               | Core strategy            |
| Example              | Merge Sort, Binary Search | Fibonacci, Knapsack, LCS |

---

## 🚧 8. Common Pitfalls

* Forgetting to handle base case → infinite recursion.
* Not combining results properly (e.g., wrong merge logic).
* Using inefficient combine step (causing O(n²)).
* Stack overflow for large inputs (use iteration/stack in those cases).

---

## 📚 9. Real-World Applications

* **Sorting**: Merge Sort, Quick Sort
* **Searching**: Binary Search
* **Numerical**: FFT, Matrix multiplication
* **Computational Geometry**: Closest pair, Convex Hull
* **AI/ML**: Minimax for Game Trees (Chess, Tic-Tac-Toe)
* **Divide-and-Rank**: Inverted index construction (search engines)

---

## 🧠 10. Advanced Extensions

* **Multithreaded Divide & Conquer**: Perfect for parallelism (e.g., Fork/Join frameworks in Java).
* **MapReduce**: Large-scale distributed version of Divide and Conquer (used in Big Data).
* **Tiling Recursion**: Used in optimizing cache locality in matrix operations.


### 🔍 Algorithm Explanation: 108. Convert Sorted Array to BST

**Goal:** Convert a sorted array into a height-balanced Binary Search Tree (BST).

---

### 💡 **Divide & Conquer Strategy**

1. **Base Case:**

   * If array is empty → return `null`.

2. **Divide:**

   * Pick the **middle element** as root → ensures balance.

3. **Conquer:**

   * Recursively do the same for:

     * **Left subarray** → left child
     * **Right subarray** → right child

4. **Combine:**

   * Link left and right subtrees to the root node.

---

### 📈 Time & Space Complexity

| Metric               | Value              |
| -------------------- | ------------------ |
| **Time Complexity**  | `O(n)`             |
| **Space Complexity** | `O(log n)` (stack) |

* **`O(n)`**: Each node is visited once.
* **`O(log n)`**: Recursive call stack depth (balanced tree).

---

class TreeNode {
  val: number;
  left: TreeNode | null;
  right: TreeNode | null;

  constructor(val?: number, left?: TreeNode | null, right?: TreeNode | null) {
    this.val = val ?? 0;
    this.left = left ?? null;
    this.right = right ?? null;
  }
}

function sortedArrayToBST(nums: number[]): TreeNode | null {
  if (!nums.length) return null;

  const mid = Math.floor(nums.length / 2);
  const root = new TreeNode(nums[mid]);

  root.left = sortedArrayToBST(nums.slice(0, mid));
  root.right = sortedArrayToBST(nums.slice(mid + 1));

  return root;
}

Here's a line-by-line explanation of the code:

---

### 🌳 TreeNode Class

```ts
class TreeNode {
  val: number;
  left: TreeNode | null;
  right: TreeNode | null;
```

* Defines a node of a binary tree with:

  * `val`: current node value.
  * `left` and `right`: children nodes (or null).

```ts
  constructor(val?: number, left?: TreeNode | null, right?: TreeNode | null) {
    this.val = val ?? 0;
    this.left = left ?? null;
    this.right = right ?? null;
  }
}
```

* Constructor allows optional inputs.
* Uses `??` to provide defaults if undefined.

---

### 🔁 Main Function

```ts
function sortedArrayToBST(nums: number[]): TreeNode | null {
  if (!nums.length) return null;
```

* Base case: if array is empty → no node to create.

```ts
  const mid = Math.floor(nums.length / 2);
  const root = new TreeNode(nums[mid]);
```

* Middle element becomes the **root** to ensure balance.

```ts
  root.left = sortedArrayToBST(nums.slice(0, mid));
  root.right = sortedArrayToBST(nums.slice(mid + 1));
```

* **Left half** of array builds left subtree.
* **Right half** builds right subtree.
* Recursive calls do the same at each level.

```ts
  return root;
}
```

Here’s the solution for **LeetCode 148. Sort List** using the **Divide and Conquer (Merge Sort)** approach.

---

### ✅ Problem:

Sort a singly linked list in **O(n log n)** time using constant space complexity.

---

### 💡 Algorithm: Merge Sort (Divide & Conquer)

1. **Divide** the list into two halves using slow & fast pointers.
2. **Recursively sort** both halves.
3. **Merge** the sorted halves.

---

### ✅ Code (TypeScript/JavaScript)

```ts
class ListNode {
  val: number;
  next: ListNode | null;

  constructor(val?: number, next?: ListNode | null) {
    this.val = val ?? 0;
    this.next = next ?? null;
  }
}

function sortList(head: ListNode | null): ListNode | null {
  if (!head || !head.next) return head;

  // 1. Split list into two halves
  let slow = head, fast = head, prev = null;
  while (fast && fast.next) {
    prev = slow;
    slow = slow.next!;
    fast = fast.next.next;
  }
  prev!.next = null; // cut the list

  // 2. Sort each half
  const left = sortList(head);
  const right = sortList(slow);

  // 3. Merge sorted halves
  return merge(left, right);
}

function merge(l1: ListNode | null, l2: ListNode | null): ListNode | null {
  const dummy = new ListNode();
  let curr = dummy;

  while (l1 && l2) {
    if (l1.val < l2.val) {
      curr.next = l1;
      l1 = l1.next;
    } else {
      curr.next = l2;
      l2 = l2.next;
    }
    curr = curr.next;
  }

  curr.next = l1 || l2;
  return dummy.next;
}
```

---

### 🧪 Test Case

```ts
// Input: [4,2,1,3]
// Output: [1,2,3,4]
```

---

### 📈 Time and Space Complexity

* **Time:** O(n log n) — from divide + merge steps
* **Space:** O(log n) — recursion stack (not extra memory)

### 🔍 Explanation of 148. Sort List using **Divide and Conquer (Merge Sort)**

---

### 🧠 Idea:

We apply **merge sort** to a linked list:

* **Divide:** Use slow & fast pointers to find the middle.
* **Conquer:** Recursively sort left and right halves.
* **Combine:** Merge the two sorted lists.

---

### 🔁 Step-by-step:

1. **Base case:**

```ts
if (!head || !head.next) return head;
```

* If the list is empty or has only one node, it’s already sorted.

2. **Find Middle (Divide Step):**

```ts
let slow = head, fast = head, prev = null;
while (fast && fast.next) {
  prev = slow;
  slow = slow.next!;
  fast = fast.next.next;
}
prev!.next = null;
```

* `slow` reaches mid, `fast` reaches end.
* `prev.next = null` splits the list into 2 halves.

3. **Recursive Sort (Conquer Step):**

```ts
const left = sortList(head);
const right = sortList(slow);
```

* Recursively sort both halves.

4. **Merge Sorted Halves (Combine Step):**

```ts
return merge(left, right);
```

* Merge the two sorted halves using helper `merge()`.

---

### 🧩 `merge()` Function:

```ts
while (l1 && l2) {
  if (l1.val < l2.val) {
    curr.next = l1;
    l1 = l1.next;
  } else {
    curr.next = l2;
    l2 = l2.next;
  }
  curr = curr.next;
}
curr.next = l1 || l2;
```

* Compare nodes and link the smaller one.
* Add remaining nodes if any.

---

### 📊 Complexity

* **Time:** `O(n log n)` – from log(n) splits and O(n) merges
* **Space:** `O(log n)` – recursion stack only (no extra memory for arrays)




