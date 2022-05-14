# `spawn` 函数(`Async` 函数实现原理)

> ## 说明：`spwan` 函数--自动执行器，需先了解 `Generator` 函数，`Async/await` 是 `Generator` 函数的语法糖

```js
function spawn(genF) {
  return new Promise((resolve, reject) => {
    var gen = genF();

    function step(nextF) {
      try {
        var next = nextF();
      } catch (e) {
        return reject(e);
      }

      if (next.done) {
        return resolve(next.value);
      }

      Promise.resolve(next.value).then(
        (v) => {
          step(() => gen.next(v));
        },
        (e) => {
          step(() => gen.throw(e));
        }
      );
    }

    step(() => {
      gen.next(undefined);
    });
  });
}
```
