---
title: Git 筆記
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
进入到旧仓库目录，通过mirror参数推送到新的Repository

```
cd [old repository]
git push --mirror [new repository url]
```
这样就会把旧仓库原样的复制到新仓库上，包括所有的分支、提交记录等等


## <center>解决fatal: refusing to merge unrelated histories</center>

Git 再合併兩個倉庫或兩個分支時，有時候會出現這個錯誤:
`fatal: refusing to merge unrelated histories`

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



