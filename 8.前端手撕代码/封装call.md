# 封装 call

```js
Function.prototype.myCall = function (context) {
  let context = context || window;
  context.fn = this;

  let args = [...arguments].slice(1);
  let result = context.fn(...args);
  delete context.fn;

  return result;
};
```
