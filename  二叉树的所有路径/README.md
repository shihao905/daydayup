### 二叉树的所有路径

给定一个二叉树，返回所有从根节点到叶子节点的路径。

说明: 叶子节点是指没有子节点的节点。

示例:
```
输入:

   1
 /   \
2     3
 \
  5

输出: ["1->2->5", "1->3"]

解释: 所有根节点到叶子节点的路径为: 1->2->5, 1->3

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/binary-tree-paths

```
```js
// 树结构
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {string[]}
 */
```
#### 方法一：深度优先搜索（DFS）
[BFS & DFS 算法介绍](https://zhuanlan.zhihu.com/p/40151973)
```js
var binaryTreePaths = function(root) {
    let paths = []
    function getPath(root, path){
        if (root) {
            path += root.val
            if (root.right === null && root.left === null) {
                paths.push(path)
            } else {
                path += '->'
                getPath(root.left, path)
                getPath(root.right, path)
            }
        }
    }
    getPath(root, '')
    return paths
};
```
#### 方法一：广度优先搜索（BFS）
```js
var binaryTreePaths = function(root) {
    let paths = []
    if (root === null) {
      return paths
    }
    const node_arr = [root]
    const path_arr = [root.val]

    while (node_arr.length) {
      const node = node_arr.shift()
      const path = path_arr.shift()

      if (node.left === null && node.right === null) {
        paths.push(path) 
      } else {
        if (node.left !== null) {
          node_arr.push(node.left)
          path_arr.push(path + '->' + node.left.val.toString())
        }
        if (node.right !== null) {
          node_arr.push(node.right)
          path_arr.push(path + '->' + node.right.val.toString())
        }
      }
    }
    return paths.re
};
```