# `new`的过程

## 原理

> 1. 创建一个空对象<br/>
> 2. 链接到原型<br/>
> 3. 绑定 this<br/>
> 4. 返回一个新对象<br/>

```js
function create() {
  let obj = Object.create();
  let Con = [].shift.call(arguments);
  obj._proto_ = Con.prototype;
  let result = Con.apply(obj, arguments);
  return typeof result === "object" ? result : obj;
}
```
