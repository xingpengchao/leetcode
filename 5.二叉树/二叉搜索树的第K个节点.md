# 二叉搜索树第 K 个节点

## 来源

> 剑指 Offer: [传送门](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

## 思路

> 利用二叉搜索树的中序遍历是一个递增序列来解决，用数组存储遍历结果，返回第 k 个节点

## 代码

```js
function KthNode(pRoot, k) {
  if (pRoot == null || k < 1) {
    return null;
  }

  const arr = [];

  //中序遍历
  function getTree(root) {
    if (root.left) {
      getTree(root.left);
    }
    arr.push(root);
    if (root.right) {
      getTree(root.right);
    }
  }

  getTree(pRoot);

  return arr[k - 1];
}
```
