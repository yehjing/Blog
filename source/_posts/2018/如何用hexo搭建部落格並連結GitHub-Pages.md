---
title: 如何用hexo搭建部落格並連結GitHub Pages
date: 2018-05-25 16:11:01
tags: Hexo
---

## <center>如何用hexo搭建部落格並連結GitHub Pages</center>

## <center> Hexo 簡介與安裝</center>
### <center>什麼是 Hexo</center>
Hexo 是一個快速、簡單且強大的網誌框架。Hexo 使用 Markdown（或其他渲染引擎）解析您的文章，並在幾秒鐘內，透過漂亮的主題產生靜態檔案。

### <center>安裝</center>
首先電腦必須安裝下列軟體:

* [Node.js](https://nodejs.org/en/)
* [Git](https://git-scm.com/)

安裝完成後透過終端機執行以下指令，藉由npm即可完成 Hexo 的安裝。
```
$ npm install -g hexo-cli
```

### <center>建立</center>

創建我的部落格:
```cmd
$ hexo init blog        //創建一個名為blog的資料夾
$ cd blog               //切換到剛創建的資料夾路徑
$ npm install           //執行npm install
$ npm install hexo-deployer-git --save      //git部署插件

```
建立完成後資料夾內會有以下檔案:
```cmd
.
├── _config.yml         //主要設定檔
├── package.json
├── node_modules        //相依套件
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts          //撰寫的所有文章都放在這個資料夾
└── themes              //主題
```
`_config.yml` 是 Hexo 主要設定檔 可修改網站[配置](https://hexo.io/zh-tw/docs/configuration.html)

此時在 blog 資料夾下執行:
```cmd
$ hexo server  
```
這時打開瀏覽器在網址列輸入 localhost:4000 就可以看到自己剛創建好的部落格啦。



---

## <center>用 GitHub Pages 與 Hexo 相聯</center>

### <center>創建新的倉庫並與 Hexo 關聯</center>
首先，先創建一個 GitHub 的帳號，然後創建一個新的倉庫。

{% asset_img new_repo.png %}

接著在站點配置文件`_config.yml`找到`deploy`這個欄位。

{% asset_img deploy.png %}

這裡配置文件的設定就是給`hexo d`這個指令做相對應的配置，讓hexo知道你要把blog部屬到哪個位置。

接著執行以下3個指令:

```cmd
$ hexo g        //生成靜態檔案
$ hexo d        //佈署至關聯的GitHub
```
此時在GitHub的新倉庫裡應該會看到剛剛所佈署的靜態文件。

### <center>GitHub Pages</center>

在GitHub倉庫中找到Settings選項。

{% asset_img settings.png %}

將畫面往下拉找到GitHub Pages，選擇master branch，選擇好後點擊save，這時重新整理頁面，就能看到自己GitHub Pages的網址了，點擊聯結進去後就是一個自己新創好的部落格囉!

{% asset_img github-pages.png %}

之後發表完新的文章後一樣是`hexo g`轉成靜態文件，然後再`hexo d`佈署到GitHub就可以在GitHub Pages看到自己所發表的文章囉!

---

## <center>相關連結</center>

相關的站點[文件設定](https://hexo.io/zh-tw/docs/configuration.html)及[主題更換](https://hexo.io/zh-tw/docs/themes.html)在Hexo官方文件中有詳細說明。

[Hexo官方文件](https://hexo.io/docs/index.html)
