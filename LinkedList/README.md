# Recursion(top to down)

## 第一种类型:

### 子问题类型相同, base case 相同

- 例如(two branches): 
  - helper(root.left)
  - helper(root.right)

- 相同base case
  - root == null

### leetcode:

tree

---

## 第二种类型:

### 子问题类型不同, base case 分类讨论

- 例如(two branches):
  - helper(index + 1)
  - hleper(index + 2)
- 不同base case
  - 分别对两个branches设置base case

### leetcode:

91

