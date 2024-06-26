# LEETCODE-Trees-1382
Sure, let's do a dry run of the `Solution` class to see how it balances a given Binary Search Tree (BST).

### Class Definition and Methods
- **balanceBST(TreeNode root):** This method initiates the balancing of the BST. It collects all the values from the BST in sorted order using in-order traversal and then builds a balanced BST from the sorted values.
- **inorder(TreeNode root, List<Integer> nums):** This helper method performs an in-order traversal of the BST to collect all node values in sorted order.
- **build(List<Integer> nums, int l, int r):** This helper method constructs a balanced BST from the sorted list of node values.

### Example

Let's use a small example to illustrate the process. Assume we have a BST as follows:

```
    4
   / \
  2   6
 / \
1   3
```

### Step-by-Step Dry Run

1. **Initialization:**
   - `root` points to the root node of the tree (value 4).

2. **In-order Traversal:**
   - We start with an empty list `nums = []`.
   - Call `inorder(root, nums)`:
     - Visit left subtree of 4 (root 2):
       - Visit left subtree of 2 (root 1):
         - Left child of 1 is null.
         - Add 1 to `nums`: `nums = [1]`.
         - Right child of 1 is null.
       - Add 2 to `nums`: `nums = [1, 2]`.
       - Visit right subtree of 2 (root 3):
         - Left child of 3 is null.
         - Add 3 to `nums`: `nums = [1, 2, 3]`.
         - Right child of 3 is null.
     - Add 4 to `nums`: `nums = [1, 2, 3, 4]`.
     - Visit right subtree of 4 (root 6):
       - Left child of 6 is null.
       - Add 6 to `nums`: `nums = [1, 2, 3, 4, 6]`.
       - Right child of 6 is null.

3. **Building the Balanced BST:**
   - Call `build(nums, 0, 4)`:
     - Calculate `m = (0 + 4) / 2 = 2`.
     - Create a new TreeNode with value 3 (`nums.get(2)`).
     - Build left subtree with `build(nums, 0, 1)`:
       - Calculate `m = (0 + 1) / 2 = 0`.
       - Create a new TreeNode with value 1 (`nums.get(0)`).
       - Build left subtree with `build(nums, 0, -1)` which returns null.
       - Build right subtree with `build(nums, 1, 1)`:
         - Calculate `m = (1 + 1) / 2 = 1`.
         - Create a new TreeNode with value 2 (`nums.get(1)`).
         - Build left and right subtrees with `build(nums, 1, 0)` and `build(nums, 2, 1)` which return null.
     - Build right subtree with `build(nums, 3, 4)`:
       - Calculate `m = (3 + 4) / 2 = 3`.
       - Create a new TreeNode with value 4 (`nums.get(3)`).
       - Build left subtree with `build(nums, 3, 2)` which returns null.
       - Build right subtree with `build(nums, 4, 4)`:
         - Calculate `m = (4 + 4) / 2 = 4`.
         - Create a new TreeNode with value 6 (`nums.get(4)`).
         - Build left and right subtrees with `build(nums, 4, 3)` and `build(nums, 5, 4)` which return null.

4. **Result:**
   - The resulting balanced BST is:
     ```
       3
      / \
     1   4
      \   \
       2   6
     ```

This demonstrates how the `Solution` class balances a given BST by performing an in-order traversal to get sorted node values and then constructing a balanced BST from the sorted list.
