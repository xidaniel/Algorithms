## Question:

- Given the `root` of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus sum of all keys greater than the original key in BST.

  As a reminder, a *binary search tree* is a tree that satisfies these constraints:

  - The left subtree of a node contains only nodes with keys **less than** the node's key.
  - The right subtree of a node contains only nodes with keys **greater than** the node's key.
  - Both the left and right subtrees must also be binary search trees.
  - https://leetcode.com/problems/convert-bst-to-greater-tree/

```
Example 1:
       2                        5
     /  \          -->       /    \
   1      3                 6      3
Input: root = [2,1,3]
Output: true
```

## High Level Idea:

- inorder reverse order travseral (right, root, left)
  - reverse travseral order
  - maintain a global sum

- Complexity Analysis:
  - Time: O(n)
  - Space: O(height of tree)

## Solution:

```java
class Solution {
    public TreeNode convertBST(TreeNode root) {
        int[] sum = new int[1];
        helper(root, sum);
        return root;
    }
    
    private void helper(TreeNode root, int[] sum) {
        if (root == null) {
            return;
        }
        helper(root.right, sum);
        sum[0] += root.val;
        root.val = sum[0];
        helper(root.left, sum);
    }
}
```

end.