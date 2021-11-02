# 封装 Map

> fn: 回调 context:回调作用域指定的 this

```js
Array.prototype.myMap = function (fn, context) {
  // 1. 获取调用者this,并转为数组
  let arr = [].slice.call(this);

  // 2. 遍历调用者
  let arrMap = [];
  for (let i = 0; i < arr.length; i++) {
    if (!arr.hasOwnProperty(i)) {
      continue;
    }
    arrMap.push(fn.call(context, arr[i], i, this));
  }

  return arrMap;
};
```
