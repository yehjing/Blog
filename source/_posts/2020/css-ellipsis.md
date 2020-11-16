---
title: CSS 限制字數/行數，讓過長的文字隱藏變"…"
date: 2020-11-16 20:00:02
urlname: css-ellipsis
tags: CSS
categories: CSS
---

## <center>原先效果</center>

{% asset_img text-Lorem.png %}

### HTML
```html
<div class="box">
  <span class="ellipsis">
    自方心使治了中音這成藝登過成正令裡天吸國過化式公臺向化式對件年數病天聲爸實正令飛有特做過成突是視一完
  </span>
</div>
```

### CSS
```css
.box {
  width:400px;
  margin: 600px auto;
  padding: 10px;
  border: 2px solid #000;
}
```

## <center>單行文字隱藏效果</center>

{% asset_img single-line-ellipsis.png %}

### CSS
```css
.ellipsis{
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```


## <center>多行文字隱藏效果</center>

{% asset_img multi-line-ellipsis.png %}

### CSS
```css
.ellipsis{
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 2; // 行數
  -webkit-box-orient: vertical;
  white-space: normal;
}
```




