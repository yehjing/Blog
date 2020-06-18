---
title: Git 指令筆記
date: 2020-06-18 20:00:02
urlname: git-note
tags: Git
categories: Git
---

<center>筆記一下自己公司久久會用一次的 git 指令</center>

## <center>複製倉庫</center>

```
git clone --bare [old repository url]
```
進入到倉庫目錄，通過 mirror 參數推送到新的 Repository

```
cd [old repository]
git push --mirror [new repository url]
```
這樣就會把舊倉庫原樣的複製到新倉庫上，包括所有的分支、提交記錄等等


## <center>解决fatal: refusing to merge unrelated histories</center>

Git 再合併兩個倉庫或兩個分支時，有時候會出現這個錯誤: `fatal: refusing to merge unrelated histories`

解決方法:
```
git merge master --allow-unrelated-histories
```

## <center>提交空的commit</center>

```
git clone [repository url]
cd [folder]
git commit --allow-empty -m 'initial'
git push
```



