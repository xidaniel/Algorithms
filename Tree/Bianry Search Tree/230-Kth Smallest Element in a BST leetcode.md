## Question:

- Given a binary search tree, write a function `kthSmallest` to find the **k**th smallest element in it.

   

  **Example 1:**

  ```
  Input: root = [3,1,4,null,2], k = 1
     3
    / \
   1   4
    \
     2
  Output: 1
  ```

## High Level Idea:

- inorder order travseral
  - maintain a global k

- Complexity Analysis:
  - Time: O(n)
  - Space: O(height of tree)


## Solution

- solution 1:

```java
class Solution {
    public int kthSmallest(TreeNode root, int k) {
        int[] kth = new int[]{k};
        int[] result = new int[1];
        helper(root, kth, result);
        return result[0];
    }
    
    private void helper(TreeNode root, int[] kth, int[] result) {
        if (root == null) {
            return;
        }
        helper(root.left, kth, result);
        if (--kth[0] == 0) {
            result[0] = root.val;
        }
        helper(root.right, kth, result);
    }
}
```

- another solution 2:

```java
// notice 0 is magic number like LCA
class Solution {
    public int kthSmallest(TreeNode root, int k) {
        int[] kth = new int[]{k};
        return helper(root, kth);
    }
    
    private int helper(TreeNode root, int[] kth) {
        if (root == null) {
            return 0;
        }
        
        int left = helper(root.left, kth);
        if (--kth[0] == 0) {
            return root.val;
        }
        int right = helper(root.right, kth);
        
        if (left == 0 && right == 0) {
            return 0;
        }
        
        return left == 0 ? right : left;
    }
}
```

end.