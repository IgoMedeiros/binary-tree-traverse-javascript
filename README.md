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

---


# Binary Tree Inorder Traversal

This repository contains **recursive** and **iterative** implementations for the **inorder traversal** of a binary tree. Inorder traversal is a depth-first search where nodes are visited in the order: **left subtree → root → right subtree**.

---

## Problem Description

### Inorder Traversal
For a binary tree, the **inorder traversal** visits nodes in the following sequence:
1. Traverse the **left subtree**.
2. Visit the **current node**.
3. Traverse the **right subtree**.

#### Example:
Given the binary tree:

```
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

The inorder traversal is: `[4, 2, 5, 1, 6, 3, 7]`.

---

## Implementations

### TreeNode Definition

```javascript
function TreeNode(val, left, right) {
    this.val = (val === undefined ? 0 : val);
    this.left = (left === undefined ? null : left);
    this.right = (right === undefined ? null : right);
}
```
The `TreeNode` class defines the structure of each node in the binary tree:
- `val`: The value of the node.
- `left`: Reference to the left child node.
- `right`: Reference to the right child node.

---

### Recursive Implementation

```javascript
const inorderTraversalRecursive = function(root) {
    const result = [];

    const traverseNode = (node) => {
        if (!node) return; // Base case: stop at null nodes
        traverseNode(node.left); // Traverse left subtree
        result.push(node.val); // Visit current node
        traverseNode(node.right); // Traverse right subtree
    };

    traverseNode(root);

    return result;
};
```

#### **Explanation**:
1. A helper function `traverseNode` is used to handle the recursive traversal.
2. If the node is `null`, the recursion stops.
3. The function processes the left subtree, visits the current node, and then processes the right subtree.
4. The traversal results are collected in the `result` array, which is returned at the end.

---

### Iterative Implementation

```javascript
var inorderTraversalIterative = function(root) {
    const result = [];
    const stack = [];
    let current = root;

    while (current || stack.length > 0) {
        while (current) {
            stack.push(current); // Push nodes to the stack to explore the left subtree
            current = current.left;
        }

        current = stack.pop(); // Visit the top node on the stack
        result.push(current.val); // Add the node's value to the result
        current = current.right; // Move to the right subtree
    }

    return result;
};
```

#### **Explanation**:
1. Use a stack to simulate the recursion process.
2. Navigate to the leftmost node, pushing nodes onto the stack.
3. Process the top node on the stack, then move to the right subtree.
4. Repeat until all nodes are processed.

---

## Time and Space Complexity

| Implementation        | Time Complexity | Space Complexity |
|------------------------|-----------------|------------------|
| **Recursive**          | \( O(n) \)      | \( O(h) \)       |
| **Iterative**          | \( O(n) \)      | \( O(h) \)       |

### **Time Complexity**
- \( O(n) \): Both implementations visit each node exactly once, where \( n \) is the number of nodes in the tree.

### **Space Complexity**
- \( O(h) \): The space complexity depends on the height \( h \) of the tree:
  - **Recursive**: The recursion stack depth is proportional to the height of the tree.
  - **Iterative**: The stack used to store nodes also grows proportionally to the tree's height.

In the best case (balanced tree), \( h = \log n \). In the worst case (skewed tree), \( h = n \).

---

## Example Usage

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

console.log(inorderTraversalRecursive(root)); // Output: [4, 2, 5, 1, 6, 3, 7]
console.log(inorderTraversalIterative(root)); // Output: [4, 2, 5, 1, 6, 3, 7]
```

---

## Key Differences Between Recursive and Iterative Solutions

| Feature                | Recursive Approach          | Iterative Approach         |
|------------------------|-----------------------------|----------------------------|
| **Readability**        | More concise and natural    | Slightly more complex      |
| **Stack Usage**         | Implicit (call stack)       | Explicit (custom stack)    |
| **Reuse**              | Requires fresh state setup  | Easy to reuse for multiple inputs |

---

## License

This code is distributed under the MIT License.
```

This `README.md` provides a detailed explanation of the problem, the recursive and iterative solutions, and their time and space complexities, ensuring clarity and depth.