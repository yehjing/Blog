---
title: JS 複製 DIV 內容
date: 2019-04-19 15:30:12
tags: JavaScript
---

{% asset_img copyPaste.gif %}

## <center>如何使用 JavaScript 實現複製 DIV 內的內容</center>

1.創建要附加到文檔的 `<textarea>` 元素。將其值設置為我們要復製到剪貼板的字符串。
2.將所述 `<textarea>` 元素附加到當前HTML文檔
3.使用 `HTMLInputElement.select()` 選擇 `<textarea>` 元素的內容。
4.使用 `Document.execCommand('copy')` 將 `<textarea>` 的內容複製到剪貼板。
5.從文檔中刪除 `<textarea>` 元素。


```js
<div id="copyArea">Copy & Paste</div>
<button onclick="copy()">複製</button>

copy = () => {
  const text = document.getElementById('copyArea').innerText
  const copyToClipboard = str => {
    const el = document.createElement('textarea')
    el.value = str
    document.body.appendChild(el)
    el.select()
    document.execCommand('copy')
    document.body.removeChild(el)
  }
  copyToClipboard(text)
}
```
