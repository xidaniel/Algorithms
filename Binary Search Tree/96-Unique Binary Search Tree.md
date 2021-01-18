+++
author = "Xi Wang"
title = "Unique Binary Search Trees"
tags = ["Tree", 
		"BST",
]
date =  "2021-01-17"
description = "BST property."
categories = [
    "Algorithm",
"DP"
]
draft = false
image = ""

+++
---
## Question:

Given *n*, how many structurally unique **BST's** (binary search trees) that store values 1 ... *n*?

**Example:**

```
Input: 3
Output: 5
Explanation:
Given n = 3, there are a total of 5 unique BST's:

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
```


## High Level Idea:

- Dynamic Programming
  - Base Case:
    - 0 --> 1
    - 1 --> 1
  - Induction Rule:
    -  M[i] = sum{M[ j ] * M[ n - j - 1 ]}, i from 1 to n,  j from 0 i - 1
- Complexity Analysis:
  - Time: O(n^2)
  - Space: O(n)



## Simulation:

```java
/*
n      当前节点 j           左子树节点    右子树节点
0           0                  0            0
1           1                  0            0
2           1                  0            1
            2                  1            0
3           1                  0            2
            2                  1     				1
            3   				       2						0

**Induction Rule:**   sum{左子树节点( j ) * 右子树节点( n - j - 1) },  j from 0 to i - 1
```

```java
/*
              i 
index  0   1   2    3    4
num    0   1   2    3    4
M    [ 1   1   2          ]
               j
```


## **Solution:**

```java
class Solution {
    public int numTrees(int n) {
        int[] M = new int[n + 1];
        M[0] = 1;
        for (int i = 1; i <= n; i++) {
            for (int j = 0; j < i; j++) {
                M[i] += M[j] * M[i - j - 1];
            }
        }
        return M[M.length - 1];
    }
}
```

end.
