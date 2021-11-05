# `Promise`封装异步上传图片

```js
function loadImageAsync(url) {
  return new Promise(function (resolve, reject) {
    let image = new Image();
    image.onload = function () {
      resolve(image);
    };

    image.onerror = function () {
      reject(new Error("Could not load image at" + url));
    };

    image.src = url;
  });
}
```
