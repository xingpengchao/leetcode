# `thunk` 函数(`Generator` 函数实现自动流程管理原理)

## 说明

> Thunk 函数是用来解决 JS 中传名调用的一种实现方式</br>
> Thunk 函数是一个单参数函数，只接受回调函数作为参数</br>
> Thunk 函数用于 Generator 函数的自动流程管理</br>

(ES5)

```js
var Thunk = function (fn) {
  return function () {
    var args = Array.prototype.slice.call(arguments);

    return function (callback) {
      args.push(callback);
      return fn.apply(this, args);
    };
  };
};
```

(ES6)

```js
const Thunk = function(fn){
  return fucntion(...args){
    return function(callback){
      return fn.call(this, ...args, callback);
    }
  }
}
```
