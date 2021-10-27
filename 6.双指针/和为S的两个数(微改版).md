# 和为 S 的两个数(微改版)

> 题目描述： 在递增数组中找出两个之和的数，返回乘积最小的两项

## 来源

> 剑指 Offer: [传送门](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

## 双指针类题目通用思路

> 1. 确定双指针位置(都在起始位置、一个在起始一个在末尾)
> 2. 确定终止条件(双指针重合、high 走到末尾)
> 3. while 语句中的条件判断(双指针走向 =>同向走、向中间靠拢)

## 思路(类似于二分查找)

> 1. 确定双指针位置(一个在起始、一个在末尾)
> 2. 确定终止条件(双指针重合)
> 3. while 语句中的条件判断(双指针向中间聚拢)

## 代码

```js
function FindNumbersWithSum(arr, sum) {
  let low = 0,
    high = arr.length - 1;
  let res = [];

  while (low < high) {
    let current = arr[low] + arr[high];

    if (sum === current) {
      res.push(arr[low]);
      res.push(arr[high]);
      break;
    } else if (current < sum) {
      low++;
    } else if (current > sum) {
      high--;
    }
  }

  return res;
}
```
