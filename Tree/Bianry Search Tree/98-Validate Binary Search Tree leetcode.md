## Question:


Given the `root` of a binary tree, *determine if it is a valid binary search tree (BST)*.

A **valid BST** is defined as follows:

- The left subtree of a node contains only nodes with keys **less than** the node's key.
- The right subtree of a node contains only nodes with keys **greater than** the node's key.
- Both the left and right subtrees must also be binary search trees.

```
Example 1:
       2
     /  \
   1      3
Input: root = [2,1,3]
Output: true
```

## High Level Idea:

- recursion (bottom-up)
  - subproblem:
    - left subtree and right subtree are BST (the current root.val in given range)
  - recursion rule:
    - if current root.val not in given range, ---> return false
    - return: left && right
  - base case:
    - root == null ---> true

- Complexity Analysis:
  - Time: O(n)
  - Space: O(height of tree)

## Simulation:

```java
/*
                               root [-infi, +infi]
                              /                  \
                 left [-infi, root.val) 	right (root.val, +infi]
                 /                  \
left [-infi, left.val)     right (left.val, root.val)         ....
```



## Solution:

```java
class Solution {
    public boolean isValidBST(TreeNode root) {
      long lowBoundary = Long.MIN_VALUE;
      long highBoundary = Long.MAX_VALUE;
      return helper(root, lowBoundary, highBoundary);
    }
  
    private boolean helper(TreeNode root, long lowBoundary, long highBoundary) {
      if (root == null) {
        return;
      }
      if (root.val <= lowBoundary || root.val >= highBoundary) {
        return false;
      }
      return helper(root.left, lowBoundary, root.val) && helper(root.right, root.val, highBoundary);
    }  
}
```

end.