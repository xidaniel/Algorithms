## Question:

Given the `root` of a **complete** binary tree, return the number of the nodes in the tree.

According to **[Wikipedia](http://en.wikipedia.org/wiki/Binary_tree#Types_of_binary_trees)**, every level, except possibly the last, is completely filled in a complete binary tree, and all nodes in the last level are as far left as possible. It can have between `1` and `2^h` nodes inclusive at the last level `h`.

**Example 1:**

```
Input: root = [1,2,3,4,5,6]
Output: 6
```

**Example 2:**

```
Input: root = []
Output: 0
```

## High Level Idea:

- Recursion
  - subproblems:
    - left subtree and right subtree
  - Recursion rule;
    - if leftHeight == rightHeight --> calculate nodes: 2^h - 1
    - leftSubtree nodes + rightSubtree nodes + 1;
  - Base Case:
    - root == null
- Complexity Analysis:
  - Time: O(log(n)^2)
  - Space: O(log(n))

## Simulation:

none

## **Solution:**

```java
class Solution {
    public int countNodes(TreeNode root) {
        if (root == null) {
            return 0;
        }
      //this is a trick to make code consise: using true or false to represent left or right
        int leftHeight = getHeight(root, true);
        int rightHeight = getHeight(root, false);
        if (leftHeight == rightHeight) {
          // 2^n == 1 << h
            return (1 << leftHeight) - 1;
        } 
        return countNodes(root.left) + countNodes(root.right) + 1; 
    }
    
    private int getHeight(TreeNode node, boolean isLeft) {
        if (node == null) {
            return 0;
        }
        node = isLeft == true ? node.left : node.right;
        return getHeight(node, isLeft) + 1;
    }
}
```

end.