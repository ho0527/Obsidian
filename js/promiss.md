
Promises 容器
從 ECMAScript2015 起，JavaScript 支援 Promise 物件，允許您控制延遲和異步操作的流程。

Promise 有以下幾種狀態:

pending：等待中，為初始之狀態，即不是 fulfilled 也不是 rejected。
fulfilled：已實現，表示操作成功完成。
rejected：已拒絕，表示操作失敗。
settled：已完成，表示 Promise 狀態為已實現或已拒絕，但不是等待中。
使用 XHR 載入圖檔
這裏有個簡單的範例，使用了 Promise 物件與及 XMLHttpRequest 來載入 MDN GitHub promise-test repository 中的一張圖檔。你也可以觀看結果。 每一步都有註解來讓您慢慢理解 Promise 物件與及 XHR 架構。 下面的版本沒有註解，但藉由觀察 Promise 物件的變動您或許可以對 promise 物件有所了解:

JS
Copy to Clipboard

function imgLoad(url) {
  return new Promise(function (resolve, reject) {
    var request = new XMLHttpRequest();
    request.open("GET", url);
    request.responseType = "blob";
    request.onload = function () {
      if (request.status === 200) {
        resolve(request.response);
      } else {
        reject(
          Error(
            "Image didn't load successfully; error code:" + request.statusText,
          ),
        );
      }
    };
    request.onerror = function () {
      reject(Error("There was a network error."));
    };
    request.send();
  });
}