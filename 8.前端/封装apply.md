# 封装 apply

```js
Function.prototype.myApply = function (context) {
  let context = context || window;
  context.fn = this;

  let result;
  if (arguments[1]) {
    result = context.fn(...arguments[1]);
  } else {
    result = context.fn();
  }
  delete context.fn;

  return result;
};
```
