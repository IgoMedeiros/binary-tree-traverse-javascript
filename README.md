# Binary Tree Preorder Traversal

This repository contains a JavaScript implementation of a **preorder traversal** algorithm for binary trees. The implementation uses an iterative approach with a stack to traverse the tree and collect node values in preorder.

## Preorder Traversal Overview

Preorder traversal is a depth-first traversal method where nodes are visited in the following order:
1. Visit the **current node**.
2. Traverse the **left subtree**.
3. Traverse the **right subtree**.

### Example:
For the following binary tree:

```
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

The preorder traversal output is: `[1, 2, 4, 5, 3, 6, 7]`.

## Code Explanation

### TreeNode Definition

```javascript
function TreeNode(val, left, right) {
    this.val = (val === undefined ? 0 : val);
    this.left = (left === undefined ? null : left);
    this.right = (right === undefined ? null : right);
}
```

The `TreeNode` function defines the structure of a binary tree node. Each node contains:
- `val`: the value of the node.
- `left`: a reference to the left child node (default is `null`).
- `right`: a reference to the right child node (default is `null`).

### Preorder Traversal Function

```javascript
const preorderTraversal = function(root) {
    const result = [];
    const stack = [];

    if (root) stack.push(root);

    while (stack.length) {
        const node = stack.pop();
        result.push(node.val);

        if (node.right) stack.push(node.right);
        if (node.left) stack.push(node.left);
    }

    return result;
};
```

#### Steps:
1. Initialize an empty `result` array to store the traversal result and a `stack` to simulate recursion.
2. If the root is not null, push it to the stack.
3. While the stack is not empty:
   - Pop the top node from the stack.
   - Add its value to the `result`.
   - Push the right child to the stack (if it exists).
   - Push the left child to the stack (if it exists).
4. Return the `result` array containing the preorder traversal.

### Test Case

```javascript
const root = {
    val: 1,
    left: {
        val: 2,
        left: { val: 4 },
        right: { val: 5 }
    },
    right: {
        val: 3,
        left: { val: 6 },
        right: { val: 7 }
    }
};

console.log(preorderTraversal(root)); // Output: [1, 2, 4, 5, 3, 6, 7]
```

The test case demonstrates the traversal of a binary tree and outputs the preorder sequence.

## How to Run

1. Copy the code into a JavaScript environment (e.g., a browser console or Node.js).
2. Define a binary tree structure (like the example above).
3. Call the `preorderTraversal` function with the tree's root node.
4. View the preorder traversal output.

## Notes

- This implementation is **iterative**, avoiding the overhead of recursion and providing better control over the traversal process.
- It uses a **stack** to simulate the recursive behavior.
