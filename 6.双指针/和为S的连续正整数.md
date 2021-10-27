# 和为 S 的连续正整数

## 来源

> 剑指 Offer: [传送门](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

## 双指针类题目通用思路

> 1. 确定双指针位置(都在起始位置、一个在起始一个在末尾)
> 2. 确定终止条件(双指针重合、high 走到末尾)
> 3. while 语句中的条件判断(双指针走向 =>同向走、向中间靠拢)

## 思路

> 双指针与滑动窗口 => 窗口的左右两边就是两个指针，根据窗口内值之和来确定窗口的位置和宽
>
> 终止条件：双指针重合

## 代码

```js
function FindContinuousSequence(sum) {
  let low = 1,
    high = 2;
  let temp = [],
    res = [];

  while (low < high) {
    let s = ((low + high) * (high - low + 1)) / 2;

    if (s === sum) {
      let set = new Set();

      for (let i = low; i <= high; i++) {
        set.add(i);
      }

      temp = Array.from(set);
      res.push(temp);
      low++;
    } else if (s < sum) {
      high++;
    } else if (s > sum) {
      low++;
    }
  }

  return res;
}
```
