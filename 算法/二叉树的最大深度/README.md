### 二叉树的所有路径

来源：力扣（LeetCode）  
链接：[https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/](https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/)

```
给定一个二叉树，找出其最大深度。

二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

说明: 叶子节点是指没有子节点的节点。

示例：
给定二叉树 [3,9,20,null,null,15,7]，

    3
   / \
  9  20
    /  \
   15   7

返回它的最大深度 3 。

```
```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
```
#### 方法一：深度优先搜索（DFS）递归
```js
var maxDepth = function (root) {
  if (!root) {
    return 0
  } else {
    let left = maxDepth(root.left)
    let right = maxDepth(root.right)
    return Math.max(right, left) + 1
  }
}

```
#### 方法二：广度优先搜索（BFS）
```js
var maxDepth = function (root) {
  if (!root) return 0
  const queue = [root]
  let num = 1
  while (queue.length) {
    let length = queue.length
    while (length) {
      const item = queue.shift()
      if (item.left) queue.push(item.left)
      if (item.right) queue.push(item.right)
      length--
    }
    if (queue.length) num++
  }
  return num
}

```
