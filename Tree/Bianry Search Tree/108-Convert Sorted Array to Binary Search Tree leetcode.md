## Question

Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of *every* node never differ by more than 1.

```
Given the sorted array: [-10,-3,0,5,9],

One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:

      0
     / \
   -3   9
   /   /
 -10  5
```

## High Level Idea:

- recursion (bottom-up)
  - subproblem:
    - for each current root node, there are reconstructed left subtree and right subtree
    - (left , mid - 1),  (mid + 1, right)
  - recursion rule:
    - root.left = subproblem
    - root.right = subproblem
    - return root
  - base case:
    - do not have any element --> left > right

- Complexity Analysis:
  - Time: O(n)
  - Space: O(height of tree)


## Simulation

```java
/*
                                 0 [-10,-3,0,5,9]
                               /                  \
                       -10 [-10,-3]               5 [5,9]  
                       /          \
                      X           [-3]         ...
```

## Solution:

```java
class Solution {
    public TreeNode sortedArray(int[] nums) {
      return helper(nums, 0, nums.length - 1);
    }
  
    private TreeNode helper(int[] nums, int lo, int hi) {
      if (lo > hi) {
        return;
      }
      int mid = lo + (hi - lo) / 2;
      TreeNode root = new TreeNode(nums[mid]);
      root.left = helper(nums, lo, mid - 1);
      root.right = helper(nums, mid + 1, hi);
      return root;
    }  
}
```

end.