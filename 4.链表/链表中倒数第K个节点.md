# 链表中倒数第 K 个节点

## 来源

> 剑指 Offer: [传送门](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)

## 解法一：队列

## 思路

> 拿一个队列保存

```js
function findKthToTail(head, k) {
  let result = [];
  while (head) {
    result.unshift(head);
    head = head.next;
  }
  return result[k - 1];
}
```

## 解法二：双指针

## 思路

> 快指针先走 k-1 步，之后快慢指针同步走，当快指针走到最后一个结点的时候，慢指针也走到了倒数第 k 个结点

## 代码

```js
function findKthToTail(head, k) {
  if (!head || !k || k <= 0) {
    return null;
  }
  let low = head;
  let fast = head;
  for (let i = 0; i < k - 1; i++) {
    if (fast.next) {
      fast = fast.next;
    } else {
      return null;
    }
  }
  while (fast.next) {
    fast = fast.next;
    low = low.next;
  }
  return low;
}
```
