---
title: Windows server佈署、ssl 憑證申請筆記
date: 2019-12-18 11:48:25
urlname: windows-server-deploy
tags:
categories: server
---
最近幫文化部做了一個網站，由於政府部門網站上線的規定及流程繁瑣，所以想說做個筆記整理一下。

一開始拿到的 Server 作業系統是 Windows 的，本來想說沒甚麼用過 IIS 這次剛好可以嘗試看看，後來怕會出包，還是用自己比較常用的 Nginx 做為 WebSever。
## <center>什麼是演算法(Algorithm)</center>
1.安裝 WebSever 這邊選用 Nginx [Nginx官網](https://www.nginx.com/)
2.更改 Nginx 設定擋
3.起本機 (localhost) 並做弱點掃描
看看資源路徑是否正確 檔案是否有成功載入

4.CSR(Certificate Signing Request) 憑證請求檔

CN:Common Name :此欄位為你要保護的網域名稱
Organization [O]:您組織的名稱,此名稱要與您合法登記的名稱一樣
Organizational Unit:[OU]:公司部門,若沒填寫則跟Common Name相同
Locality [L]:公司所在地的城市名稱
State [ST]:公司所在地的州或郡
Country [C]:公司所在地的國家
Key Size:憑證演算法與金鑰長度

## <center>時間複雜度(Time Complexity)</center>

>時間複雜度是用來評斷演算法執行快慢的指標，通常用大 O 符號（Big O notation）來記錄時間複雜度的快慢。

要評判一個演算法的好壞，最基本的兩個指標:

* 需要消耗的時間(時間複雜度)
* 佔用記憶體空間(空間複雜度)
看到當 n 到達一定數量， O(n²) 所花時間比 O(n) 多千倍甚至萬倍。所以寫出一個好的演算法是很重要的！


## <center>重點整理<center>

* 演算法的簡單定義：輸入 + 演算法 = 輸出
* 時間複雜度：衡量演算法執行好壞的工具
* Big O：用來描述演算法在輸入 n 個東西時，總執行時間與 n 的關係
* n 是以最壞情況下做紀錄
* 在 n 非常大時，好的演算法設計可以省下非常多時間
* 演算法的速度不是以秒計算，而是以步驟次數
* 實務上，我們只會紀錄最高次方的那一項，並忽略重要項目之外的係數
