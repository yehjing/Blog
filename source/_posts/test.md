---
title: test
date: 2018-06-01 21:54:28
tags: [Express]
---

use() 是 Express 當中非常重要的方法，用途很廣，初學的我記錄下來一些相關的功能，避免之後忘記怎麼去運用。
***


## 基礎

app.use() 可以想像成一個關卡，可以在其中寫入許多個程序，像是驗證判斷等等...再透過 next() 往下執行。

```js
const app = require('express');

app.use((req, res, next) => {
  // 寫點 function
  next(); // 繼續
});
```
***


## 找不到頁面

將 app.use() 寫在各種路由的最下方，當找不到對應的路由時，就會依序往下直到執行 app.use()，並且回傳錯誤代碼 404。

```js
app.use((req, res, next) => {
  res.status(404).send('找不到頁面');
});
```
***


## 程式錯誤

這個用法比較特別一點，只能在所有路由與 app.use() 之後才定義，而且要加入第四個引數 `err`  ，當有程式出錯的時候，就會直接跳到這段內容。  

```js
app.use((err, req, res, next) => {
  res.status(500).send('錯誤訊息');
});
```
***


## 宣告靜態檔案的位置

Express 必須要宣告靜態檔案的位置，才可以在 HTML 之中使用，記得要寫在最前面，避免路由執行的時候還不知道檔案位置。

```js
app.use(express.static('public'));
// 將根目錄底下的 public 資料夾宣告為放靜態檔案的位子

app.get('/', (req, res) => {
  res.send(`
    <html>
    <head></head>
    <body>
      <h1>Title</h1>
      <img src='/img/pitcure.png'>
      // 宣告位置之後 src 就會以 public 做為起點
    </body>
    </html>
  `);
});
```
***

## 其他寫法

只是要提醒以後的自己，不要被上面的寫法綁住。

```js
const auth = (req, res, next) => {
  console.log('驗證程序之類的');
  next();
}
app.use(auth);
// 當同樣的內容要多次使用，這樣包裝方式精簡也好讀。

app.get('/', auth, use()2, use()3, ..., (req, res) => {
  res.send('2018/2/17');
});
// 也可以寫到路由的引數當中，甚至是插入多個 app.use() 並且依序執行。
```