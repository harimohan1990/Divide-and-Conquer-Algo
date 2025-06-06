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


