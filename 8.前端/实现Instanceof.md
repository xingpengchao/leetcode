# 实现`Instanceof`

## 核心：原型链的向上查找

```js
function myInstanceof(left, right) {
  if (typeof left !== "object" || left == null) return false;

  let proto = Object.getPrototypeOf(left);
  while (true) {
    if (proto == null) return false;
    if (proto === right.prototype) return true;
    proto = Object.getPrototypeOf(proto);
  }
}
```
