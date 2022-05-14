# 手撕`Promise`

> ### `Promise`简易版

```js
class Promise {
  constructor(executor) {
    this.state = "pending";
    this.value = undefined;
    this.reason = undefined;

    let resolve = (value) => {
      if (this.state === "pending") {
        this.state = "resolved";
        this.value = value;
      }
    };

    let reject = (reason) => {
      if (this.state === "pending") {
        this.state = "rejected";
        this.reason = reason;
      }
    };

    try {
      executor(resolve, reject);
    } catch (err) {
      reject(err);
    }
  }

  then(onResolved, onRejected) {
    if (this.state === "resolved") {
      onResolved(this.value);
    }

    if (this.state === "rejected") {
      onRejected(this.reason);
    }
  }
}
```
