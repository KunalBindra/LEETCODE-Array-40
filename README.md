# LEETCODE-Array-40
**Understanding the Code:**

Before we dive into the dry run, let's break down what the code does:

- **`combinationSum2`**: This is the main function that takes an array of candidates and a target sum as input. It initializes an empty list `ans` to store the final combinations. Sorts the candidates array to handle duplicates efficiently. Calls the recursive `dfs` function to find combinations.
- **`dfs`**: This is a recursive helper function that takes the starting index `s`, candidates array, target sum, current path, and answer list as input.
  - Base cases:
    - If `target` becomes negative, return as no valid combination can be formed.
    - If `target` is 0, a valid combination is found, so add the current `path` to the `ans` list.
  - Iterates over candidates from index `s` to the end:
    - Skips duplicates by checking if the current element is the same as the previous one.
    - Adds the current candidate to the `path`.
    - Recursively calls `dfs` with the updated index, target, path, and answer list.
    - Removes the current candidate from the `path` to backtrack.

**Dry Run:**

Let's consider an example:

```
candidates = [10, 1, 2, 7, 6, 1, 5]
target = 8
```

**Initial Call:**

- `combinationSum2([10, 1, 2, 7, 6, 1, 5], 8)`
- Sort the candidates: `[1, 1, 2, 5, 6, 7, 10]`
- Call `dfs(0, [1, 1, 2, 5, 6, 7, 10], 8, [], ans)`

**First Recursive Call:**

- `dfs(0, [1, 1, 2, 5, 6, 7, 10], 8, [], ans)`
  - `i = 0`, `candidates[i] = 1`, `target - candidates[i] = 7`
  - `path = [1]`
  - `dfs(1, [1, 1, 2, 5, 6, 7, 10], 7, [1], ans)`

**Second Recursive Call:**

- `dfs(1, [1, 1, 2, 5, 6, 7, 10], 7, [1], ans)`
  - `i = 1`, `candidates[i] = 1`, `target - candidates[i] = 6`
  - `path = [1, 1]`
  - `dfs(2, [1, 1, 2, 5, 6, 7, 10], 6, [1, 1], ans)`

**... and so on**

The `dfs` function will explore all possible combinations by recursively calling itself with different starting indices and updated targets. It uses backtracking to explore different paths. The `if (i > s && candidates[i] == candidates[i - 1]) continue;` line ensures that duplicate combinations are not considered.

**Key Points:**

- The code uses backtracking to explore all possible combinations.
- Sorting the candidates array and skipping duplicates helps to optimize the solution.
- The `dfs` function recursively builds the combinations by adding candidates to the `path` and removing them when backtracking.

