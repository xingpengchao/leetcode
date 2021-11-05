# 手撕`Promise.all`

```js
function promiseAll(promises) {
  return new Promise(function (resolve, reject) {
    if (!Array.isArray(promises)) {
      return reject(new Error("Promises must be an array"));
    }

    let resolvedCount = 0;
    let promiseNum = promises.length;
    let resloveValue = [];

    for (let i = 0; i < promiseNum; i++) {
      Promise.resolve(promises[i]).then(
        (value) => {
          resloveValue[i] = value;
          resolvedCount++;
          if (resolvedCount === promiseNum) {
            return resloveValue;
          }
        },
        (err) => {
          return reject(err);
        }
      );
    }
  });
}
```
